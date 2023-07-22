---
layout: page
title: Projects
---

<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
.collapsible {
  border-radius: 8px;
  background-color: #e88181;
  color: white;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  font-size: 18px;
}

.active, .collapsible:hover {
  background-color: #e46b6b;
}

.content {
  padding: 3px 15px;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.2s ease-out;
  background-color: #fcfafa;
}

</style>
<body>

<h2>Research</h2>
<br>

<button class="collapsible">Evidentiality in Squliq Atayal*</button>
<div class="content">
  <p>A preliminary account of evidentiality in the Squliq dialect of Atayal, based on the results of a translation task I conducted with Atayal speakers</p>
  <ul>
    <li><a href="https://drive.google.com/file/d/1v30dkRBWRjbmWg1YHXQvgIYqQ_x9uduM/view?usp=share_link">[Manuscript (under review)]</a> <a href="https://drive.google.com/file/d/1HPMZNzJUzBHfD_EiXirJ9cg5lLgSEmXo/view?usp=share_link">[Slides]</a></li>
  </ul>
  <br>
</div>
<button class="collapsible">Deriving the argument structure of converbs*</button>
<div class="content">
  <p>An analysis of the argument structure and clausal relationships of converb constructions in Khalkha Mongolian and Manchu</p>
  <ul>
    <li><a href="https://drive.google.com/file/d/15b0qgDJrgE9NPaOcPD4mdcqEpRkh1p9w/view?usp=share_link">[Publication]</a> <a href="https://drive.google.com/file/d/1XkGkNnGNwjWPoWaeXgyCI_w_DuDEvCSB/view?usp=share_link">[Poster]</a></li>
  </ul>
  <br>
</div>
<button class="collapsible">The case of fragment answers</button>
<div class="content">
  <p>A novel analysis of the case forms of pronominal fragment answers in response to subject <i>wh-</i> questions in English, Korean, and Serbian</p>
  <ul>
    <li><a href="https://journals.linguisticsociety.org/proceedings/index.php/PLSA/article/view/5214">[Publication]</a></li>
  </ul>
  <br>
</div>

<p style="font-size: 15px"><b>*</b> features work on endangered and/or under-described languages</p>
<br>

<h2>Endangered language documentation</h2>
<br>

<button class="collapsible">Manchu</button>
<div class="content">
  <p>Since 2021, I have been collaborating with speakers of Sibe, a dialect of Manchu to develop online documentation materials for the speaker community. These documentation materials include a  Sibe-Mandarin-English dictionary with audio recordings, an introductory phrasebook, a video archive of authentic language material, and more. All of these resources can be found on Mini Buleku (lit. 'My Dictionary'), an online platform I coded and developed to make our resources available to the community of speakers in China and abroad.</p>
  <ul>
    <li><a href="https://minibuleku.github.io/">[Mini Buleku]</a></li>
  </ul>
  <br>
</div>
<button class="collapsible">Jewish languages</button>
<div class="content">
    <p>From July 2022 to August 2023, I served as Documentation Manager of the HUC-JIR Jewish Language Project, where I led the organization's work in documenting endangered Jewish language varieties — primarily <a href="https://www.jewishlanguages.org/judeo-iranian">Judeo-Iranian</a> and <a href="https://www.jewishlanguages.org/jewish-aramaic">Jewish Neo-Aramaic</a>. For both languages, I coordinated the filming, transcription/translation, and dissemination of over 10 authentic language sample videos. I also collaborated with the community of Jewish Neo-Aramaic speakers to lay the groundwork for an online recorded dictionary, as well as a speaker of Judeo-Arabic to produce an <a href="https://youtu.be/rsPCCsw7UsQ">oral history</a> in the language. Finally, in November 2022, I applied for a grant with the Wikimedia Foundation and was awarded approximately $50,000 to create and upload content in endangered Jewish languages to the various Wikimedia Projects, including Wikimedia Commons and Wikipedia.</p>
    <ul>
        <li><a href="https://meta.wikimedia.org/wiki/Grants:Programs/Wikimedia_Community_Fund/Documenting_and_increasing_Jewish_language_representation_on_Wikimedia">[Grant]</a> <a href="https://forward.com/culture/554932/jewish-languages-iran-neo-aramaic-endangered-preservation-wikimedia">[News article]</a></li>
    </ul>
    <br>
    </div>
<script>
var coll = document.getElementsByClassName("collapsible");
var i;

for (i = 0; i < coll.length; i++) {
  coll[i].addEventListener("click", function() {
    this.classList.toggle("active");
    var content = this.nextElementSibling;
    if (content.style.maxHeight){
      content.style.maxHeight = null;
    } else {
      content.style.maxHeight = content.scrollHeight + "px";
    } 
  });
}
</script>

