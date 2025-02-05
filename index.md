---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
author_profile: true
---



Welcome to my website :tada:


This is the place where I publish my [research](/research/) and some of the [projects](/projects/) I am working on. Occasionally, I also [post](/posts/) tutorial and articles on ML and AI topics or recent research that I find fascinating.

<br>

# For recruiters
<div style="display: flex; flex-direction: column;">
<p style="margin-bottom: 0px;">Here are some directions on where to find what:</p>
<div style="display: flex; gap: 40px;">

<div>
<ul>
<li><a href="/assets/misc/Guglielmo_Gattiglio_CV.pdf">My latest CV</a></li>
<li><a href="/projects/">My Project Portfolio</a></li>
</ul>
</div>

<div>
<ul>
<li><a href="/research/">My Research</a></li>
<li><a href="/about/">Who I am</a></li>
</ul>
</div>

</div>

</div>


<br>


{% assign target_post = site.posts | where: "slug", "tex-willer-project-series" | first %}
To kickstart the website, I am planning a [_major_ series]({{ target_post.url }}) on **multimodal language models**, curating the whole pipeline: 
- data collection
- pre-processing
- label generation (using LLMs, of course)
- fine-tuning (we will experiment a lot with this)
- deployment 

<!-- {% assign target_post = site.posts | where: "slug", "tex-willer-project-series" | first %}
Check out my [first post]({{ target_post.url }}) below for more info! -->

Stay tuned!

\- Guglielmo

<br><br>