---
layout: page
title: Tools
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

/* ---- Full-screen button ---- */
.fs-btn {
  display: block;
  margin: 8px 0 0 auto;
  padding: 5px 12px;
  font-size: 14px;
  cursor: pointer;
  border: 1px solid #c55;
  border-radius: 6px;
  background: #fff;
  color: #c55;
}
.fs-btn:hover { background: #fbeaea; }

/* Real fullscreen (desktop, Android, iPad) */
.fs-wrap:fullscreen {
  background: #fcfafa;
  padding: 8px 12px;
}
.fs-wrap:fullscreen iframe {
  height: calc(100vh - 60px) !important;
  margin: 6px 0 0 !important;
}

/* Fallback overlay (iPhone Safari, or if fullscreen is blocked) */
.fs-wrap.fs-fallback {
  position: fixed;
  inset: 0;
  z-index: 99999;
  background: #fcfafa;
  padding: 8px 12px;
}
.fs-wrap.fs-fallback iframe {
  height: calc(100vh - 60px) !important;
  margin: 6px 0 0 !important;
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

<button class="collapsible">Photo Blur & Zoom</button>
<div class="content" data-src="/assets/blur-zoom.html"></div>
<br>

<button class="collapsible">Linguistics Problem Set</button>
<div class="content" data-src="/assets/pset.html"></div>
<br>

<script>
// Builds: <div class="fs-wrap"> <button> + <iframe> </div>
function buildApp(content, title) {
  var wrap = document.createElement("div");
  wrap.className = "fs-wrap";

  var btn = document.createElement("button");
  btn.type = "button";
  btn.className = "fs-btn";
  btn.textContent = "⛶ Full screen";

  var frame = document.createElement("iframe");
  frame.src = content.dataset.src;
  frame.title = title;
  frame.setAttribute("allowfullscreen", "");

  function isFull() {
    return document.fullscreenElement === wrap ||
           wrap.classList.contains("fs-fallback");
  }
  function updateLabel() {
    btn.textContent = isFull() ? "✕ Exit full screen" : "⛶ Full screen";
  }

  btn.addEventListener("click", function () {
    if (isFull()) {
      if (document.fullscreenElement) document.exitFullscreen();
      wrap.classList.remove("fs-fallback");
    } else if (wrap.requestFullscreen) {
      wrap.requestFullscreen().catch(function () {
        wrap.classList.add("fs-fallback");
        updateLabel();
      });
    } else {
      wrap.classList.add("fs-fallback");
    }
    updateLabel();
  });

  document.addEventListener("fullscreenchange", updateLabel);

  wrap.appendChild(btn);
  wrap.appendChild(frame);
  content.appendChild(wrap);
}

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
        buildApp(content, this.textContent);
      }
      content.style.maxHeight = content.scrollHeight + "px";
    }
  });
}
</script>
