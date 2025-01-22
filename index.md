---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
author_profile: true
---



Welcome to my website :) 

This is the place where I publish my [research](/research/) and some of the [projects](/portfolio/) I am working on. Occasionally, I also [post](/posts/) tutorial and articles on ML and AI topics or recent research that I find fascinating.


To kickstart it, I am planning a _major_ series on multimodal language models, curating the whole pipeline: 
- data collection
- pre-processing
- label generation (using LLMs, of course)
- fine-tuning (we will experiment a lot with this)
- deployment 

{% assign target_post = site.posts | where: "slug", "tex-willer-generation-1" | first %}
Check out my [first post]({{ target_post.url }}) below for more info!


**For recruiters**. Here are some directions on where to find what:
- My latest [CV](/assets/misc/Guglielmo_Gattiglio_CV.pdf)
- My [Portfolio](/projects/)
- My [Research](/research/)
- [Who I am](/about/)