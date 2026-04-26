---
layout: page
title: Teaching
---
<!-- 
cd C:\Users\Jacob\jkodner18.github.io
bundle exec jekyll serve 
 -->
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>

 li {
       line-height: 2.0;
 }   
        
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

</style>

<body>

<h2>Linguistics & K-12</h2>
As of 2025, I've been exploring the question of what insights from theoretical linguistics can be applied in pre-university classrooms, to inform & transform (language) pedagogy — a line of work that is relatively underexplored in both linguistics and education spaces. Below are some of my recent output for K-12 students & teachers:
<ul>
 <li>An <a href="https://drive.google.com/file/d/1SO8hN3rNEPL7aJ77xHhtBwaUNfxquW5J/view?usp=sharing">informational guide</a> for teachers that introduces ideas for bringing linguistics into the classroom.</li>
 <li>A <a href="https://docs.google.com/presentation/d/1n89c2lWBXurFI8sFrZLGKluargDcVqds5XOlU25Y5z8/edit?usp=drive_link">lesson on the linguistics of word-level stress</a>, delivered to a 7th-grade English class to supplement instruction on poetry. Special thanks to Beth Keyser for this opportunity.
</li>
 <li>A set of introductory linguistics crashcourse materials, taught to high school students at <a href="https://docs.google.com/presentation/d/1MEuvq0Itn0YTuoVcWvOu1Uw7jkXBNtdk_IsPYC5ogyc/edit?usp=drive_link">MIT Splash 2025</a> and <a href="https://docs.google.com/presentation/d/1Gn_4Kod_57-sjvaWnCwkUk4NSlypf9IkiyaveM-aTs8/edit?usp=sharing">Harvard HWeek 2025</a>, with the latter having a Mandarin-English bilingual component.</li>
 <li>Pop-up courses on <a href="https://docs.google.com/presentation/d/1Gig4xLUvgAiH9aoDImZQdctZHjPJwpb9VxAL_OQmuFE/edit?usp=sharing">phonology</a> and <a href="https://docs.google.com/presentation/d/1dset725RBrejbBzvNmchTbNuxRKJx4bTDgAn9VSicuM/edit?usp=sharing">syntax</a> taught to high school students at MIT HSSP 2026. Special thanks to Dr. Maya Honda (MIT Linguistics) for this opportunity.</li>
</ul>

<br><img style="margin-top: -20px; display: block; margin-left: auto; margin-right: auto; height: 80%; width: 80%; border-radius: 10px" src="/assets/img/ling-classroom.jpg">
<p>The above is from an English lesson I taught in 2025 at Shinkaie Elementary School (新開國小) in Miaoli, Taiwan. In this lesson, I superimposed a pitch contour (visualization of change in one's pitch) above sentences in question-answer pairs, and had students practice these together as dialogues, to build students' understanding of English intonation. See <a href="https://youtu.be/F6M11zjLJb8">here</a> for related local news coverage of my volunteering in rural Taiwan.</p>

<h2>Teaching @ Harvard</h2>
For examples of my teaching materials in linguistics at Harvard, see <a href="https://docs.google.com/presentation/d/1wJzy8XwElw87u8BQFWHq6eAhg2u7yOI1d3AE5xahisA/edit?usp=sharing">here</a>, <a href="https://docs.google.com/presentation/d/1xVeNGhg6hvWwija0yPZLaoB5Fi2ejUGfEz96Kr28-go/edit?usp=sharing">here</a>, and <a href="https://docs.google.com/presentation/d/1Jo7ezdbJngw8HyYysetKuSReFmD6StfF0-Ct_ZfedpA/edit?usp=sharing">here</a>.<br>

<button class="collapsible">LING 83: Language, Structure, and Cognition</button>
<div class="content">
  <ul>
   <li>Fall 2025 Section (10 students)</li>
   <li>Sample teaching materials [link]</li>
  </ul>
  <p><i>Course Description</i>: Even though everyone speaks or signs at least one language, the complexity of language in its structure and function is often underappreciated and misunderstood. This myth-busting class guides students to the field of linguistics. Together, we will explore how language is structured from sound to conversation, how language is related to society, and how language is processed in the brain and simulated by machines. Students will engage with linguistic data, explore language technology, and reflect on their positions in the social world through ideologies about languages and their speakers. At the end of the class, with a taste for being a linguist, students will appreciate the skills and opportunities that linguistics can offer.
</p>
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

