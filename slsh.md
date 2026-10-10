---
layout: page
title: SLSH
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
  background-color: #fcfafa;
  transition: max-height 0.2s ease-out;
  overflow: hidden;
}

.content iframe {
  width: 100%;
  height: 600px;
  border: none;
  margin: 10px 0;
}
</style>

<body>

<button class="collapsible">Item Shuffler</button>
<div class="content" data-src="/assets/item-shuffler.html"></div>
<br>

<button class="collapsible">Hat Shuffler</button>
<div class="content" data-src="/assets/hat-shuffler.html"></div>
<br>

<button class="collapsible">Label Activity</button>
<div class="content" data-src="/assets/label-activity.html"></div>
<br>

<button class="collapsible">Learning Quest</button>
<div class="content" data-src="/assets/learning-quest.html"></div>
<br>

<script>
var coll = document.getElementsByClassName("collapsible");
var i;

for (i = 0; i < coll.length; i++) {
  coll[i].addEventListener("click", function() {
    this.classList.toggle("active");
    var content = this.nextElementSibling;

    if (content.style.maxHeight) {
      content.style.maxHeight = null;
    } else {
      // Load the iframe only the first time this box is opened
      if (content.dataset.src && !content.querySelector("iframe")) {
        var frame = document.createElement("iframe");
        frame.src = content.dataset.src;
        frame.title = this.textContent;
        frame.setAttribute("allowfullscreen", "");
        content.appendChild(frame);
      }
      content.style.maxHeight = content.scrollHeight + "px";
    }
  });
}
</script>
