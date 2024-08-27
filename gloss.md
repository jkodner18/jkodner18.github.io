---
layout: page
title: Gloss2Latex
---
<!-- 
cd C:\Users\Jacob\jkodner18.github.io
bundle exec jekyll serve 
 -->

<html lang="en">
<head>
    <meta charset="UTF-8">
    <style>

        body { 
        font: 15px/1.3em 'Verdana';
        }

        td {
            font-size: 17px;
        }

        #table_id_filter {
            font-size: 17px;
            margin-bottom: 20px
        }

        input[type=search] {
            height: 25px;
        }

        .bio {
            margin-left:auto;
            margin-right:auto;
            padding-left: 5%;
            padding-right: 5%
        }
        ​

        img.center {
                margin-top: 50px;
                display:block;
                margin-left:auto;
                margin-right:auto
            }

        div.f {
                margin-top: 35px;
                margin-left:auto;
                margin-right:auto;
                text-align:center;
            }

        div.j {
            display: inline-block;
            margin-left: 0px;
            text-align: left;
        }

        div.x {
            display: inline-block;
            margin-left: 110px;
            text-align: left;
        }

        button {
            width: 150px;
            height: 60px;
            font-size: 20px;
            font-weight: bold
        }

        textarea {
            border-width: 2px;
            width: 100%;
        }

        .column {
            display: flex;
            flex: 50%;
            padding: 5px
        }

        a {
        text-decoration: none;
        }

        li {
        list-style: none;
        display: inline;
        }


        .navbar {
        padding-top: 5px;
        padding-bottom: 10px;
        color: #fff;
        text-align: center;
        }


        .nav-links a {
        color: black;
        text-align: center;
        text-decoration: none
        }

        /* LOGO */
        .logo {
        font-size: 32px;
        }
        /* NAVBAR MENU */
        .menu {
        gap: 1em;
        font-size: 20px;
        }
        .menu li:hover {
        background-color: lightgrey;
        border-radius: 5px;
        transition: 0.3s ease;
        }
        .menu li {
        padding: 5px 14px;
        display:inline-block;
        background-color: #ECECEC;
        }

    </style>
</head>

<div class = "f">
    <form>
        <h2>Plain Text</h2>
        <textarea id="input" rows="12" cols="150" name="input" placeholder=""></textarea><br>
        <h2>LaTeX</h2>
        <textarea id="output" rows="12" cols="150" name="output"></textarea><br><br>
        <div style="font-size: 20px; text-align: left">
            <input type="radio" id="linguex" name="package" value="linguex" checked="checked">
            <label for="html">linguex</label><br>
            <input type="radio" id="gb4e" name="package" value="gb4e">
            <label for="css">gb4e</label><br><br>
            <input type="checkbox" id="georgian" value="georgian">
            <label for="georgian">Georgian orthography used</label><br>
        </div>
        <br>
        <button type="button" id="sub">Convert</button><br><br>
    </form>
</div>

<script>
document.getElementById("sub").onclick = function() {gloss2latex()}

function addQuote(transl) {
    if (!['`', "'", '"'].includes(transl[0])) {
        transl = '`' + transl;
    } else {
        transl = '`' + transl.slice(1);
    }
    if (!['`', "'", '"'].includes(transl[transl.length - 1])) {
        transl += "'";
    } else {
        transl = transl.slice(0, -1) + "'";
    }
    return transl;
}

function addSc(transcr) {
    const annotations = transcr.match(/[ -=]?(Q|[A-Z1-9.]{2,})/g) || [];
    annotations.forEach(annotation => {
        annotation = annotation.trim().replace(/^-/, '').replace(/^=/, '');
        if (!isNaN(annotation)) return;
        const replacement = `\\textsc{${annotation.toLowerCase()}}`;
        transcr = transcr.replace(annotation, replacement);
    });
    return transcr;
}

function gloss2latex(input) {

   if (document.getElementById("linguex").checked){
       var package = "linguex"
    } else if (document.getElementById("gb4e").checked){
       var package = "gb4e"
    };

  var input = document.getElementById("input").value

  var output = ""


  if (!["linguex", "gb4e"].includes(package)) {
    package = "linguex";
  }

  input = input.trim().replace(/\n{3,}/g, '\n\n').replace(/ {2,}/g, ' ');

  let allGlosses = input.split("\\").filter(i => i !== "");

  allGlosses.forEach((glossSet, glossSetCount) => {
    glossSet = glossSet.trim().split("\n\n");
    const multiGloss = glossSet.length > 1;

    var glossSetCount = 0;

    glossSet.forEach((indivGloss, index) => {
      indivGloss = indivGloss.split("\n");
      const numGlossLine = indivGloss.filter(i => !i.startsWith("%")).length;
      const fourlineGloss = numGlossLine > 3;

      if (indivGloss.length < 3) return;

      let glossDict = {};
      const firstLine = indivGloss[0];
      const custLabelMatch = /^\[.+\] /.exec(firstLine);
      let custLabel = "";

      if (custLabelMatch) {
        custLabel = custLabelMatch[0].trim();
        indivGloss[0] = firstLine.replace(/^\[.+\] /, "").trim();
      }

      if (!fourlineGloss) {
        glossDict.transcr_main = indivGloss[0];
        glossDict.annotation = indivGloss[1];
        glossDict.translation = indivGloss[2];
        glossDict.comments = indivGloss.filter(i => i.startsWith("%")).join("\n");

        let transcrSign = "";
        if (!multiGloss) {
          transcrSign = package === "linguex" ? "\n\\ex.\\gll " : "\n\\begin{exe}\n\\ex \\gll ";
        } else {
          if (glossSetCount === 0) {
            transcrSign = package === "linguex" ? "\n\\ex.\\ag." : "\n\\begin{exe}\n\\begin{xlist}\n\\ex ";
          } else {
            transcrSign = package === "linguex" ? "\\bg." : "\\ex ";
          }
        }

        if (package === "linguex") transcrSign += custLabel + " ";
        glossDict.transcr_main = transcrSign + glossDict.transcr_main + "\\\\";
      } else {
        glossDict.transcr_main = indivGloss[0];
        glossDict.transcr_extra = indivGloss[1];
        glossDict.annotation = indivGloss[2];
        glossDict.translation = indivGloss[3];
        glossDict.comments = indivGloss.filter(i => i.startsWith("%")).join("\n");

        const orthoList = ["georgian"];
        var command = "";

        for (let indiv_lang of orthoList) {
            if (document.getElementById(indiv_lang).checked) {
                command = "\\text" + indiv_lang;
            }
        };

        if (command != "") {
          console.log(command)
          glossDict.transcr_main = glossDict.transcr_main.split(" ").map(word => {
            if (!(word.startsWith("[") && word.endsWith("]"))) {
              return `${command}{${word}}`;
            }
            return word;
          }).join(" ");
        }

        let transcrSign = "";
        if (glossSetCount === 0) {
          transcrSign = multiGloss ? (package === "linguex" ? "\n\\ex.\\a." : "\n\\begin{exe}\n\\begin{xlist}\n\\ex ") : (package === "linguex" ? "\n\\ex." : "\n\\begin{exe}\n\\ex ");
        } else {
          transcrSign = package === "linguex" ? "\\b." : "\\ex ";
        }

        if (package === "linguex") transcrSign += custLabel + " ";
        glossDict.transcr_main = transcrSign + "\\glll " + glossDict.transcr_main + "\\\\";
        glossDict.transcr_extra += "\\\\";
      }

      glossDict.annotation = addSc(glossDict.annotation) + "\\\\";
      glossDict.translation = package === "gb4e" ? `\\trans \\glt ${addQuote(glossDict.translation)}` : `\\glt ${addQuote(glossDict.translation)}`;

      output += glossDict.transcr_main + "\n"
    //   console.log(glossDict.transcr_main);
      if (fourlineGloss) {
        output += glossDict.transcr_extra + "\n"
        // console.log(glossDict.transcr_extra);
      }
        output += glossDict.annotation + "\n"
    //   console.log(glossDict.annotation);
      
      output += glossDict.translation + "\n"
    //   console.log(glossDict.translation);

      if (glossDict.comments) {
        output += glossDict.comments + "\n"
        // console.log(glossDict.comments);
      }

      if (package === "gb4e" && glossSetCount === glossSet.length - 1) {
        if (glossSet.length !== 1) {
            output += "\\end{xlist}" + "\n"
        //   console.log("\\end{xlist}");
        }
        output += "\\end{exe}" + "\n"
        // console.log("\\end{exe}");
      }

      glossSetCount += 1
      
    });
  });
  output_element = document.getElementById("output")
  output_element.textContent = output.slice(1)
}
</script>






