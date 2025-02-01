---
title: "Deep comics generation with multimodal LLMs"
# last_modified_at: 2016-03-09T16:20:02-05:00
categories:
  - Blog
  - Projects
tags:
  - MLLM
  - Computer vision
  - NLP
permalink: /blog/:title
excerpt: "Introducing a series of blog posts on my new project: generating novel, fake comics resembling Tex Willer. "
---

![An image of Tex Willer](https://upload.wikimedia.org/wikipedia/it/3/3e/Tex_willer_panini_comics.jpg){:.cnt}


## What's this project about

**Project aim**: to generate new Tex Willer comics for the italian language (sorry non-italian speakers - you are really missing out here). The storyline should be customizable, and this should reflect in both text and visual adaptations.

**Data**: open-source black-and-white books available on Internet Archive.

**Why**: I love Tex! I have been eagerly reading it since I was young. It was (and still is) a role model for me and had an impact in shaping the person I am. Plus, it's really a fun and captivating pastime. I own the whole `Tex - Collezione storica a colori` collection of 256 color volumes that ran from 2007 till 2015. Even though I read them all multiple times, it never gets old, and I would love to have more. It's 2025, and with a bit of luck (and skills, and data) we will attempt to do just that!

**Milestones** :
- Data preprocessing and panel extraction
- Text extraction and cleaning (labels)
- Narrative reconstruction
- Writing-style learning and story generation
- Panel generation 
- Panel temporal alignment
- In-painting to color the black-and-white panels
- [Optional] English translation
- Deployment on a self-hosted solution

_**Note**: while this project may seem "trivial", it covers many state of the art technologies and paradigms, including multimodal language models (MLLMs), diffusion, fine-tuning, and deployment on resource-constrained hardware._

## Articles in this series

More articles will be added as I find time to write them :smile:

{% assign target_post = site.posts | where: "slug", "tex-willer-generation-1" | first %}
- [{{target_post.title}}]({{ target_post.url }})
