---
title: "Deep comics generation with multimodal LLMs - Overview - Part 1"
# last_modified_at: 2016-03-09T16:20:02-05:00
categories:
  - Blog
  - Projects
tags:
  - MLLM
  - Computer vision
  - NLP
permalink: /blog/:title/
excerpt: "Introducing the first project featuring multimodal language models and diffusion - overview."
---

{% assign orig_post = site.posts | where: "slug", "tex-willer-project-series" | first %}
A new posts in the [Tex Willer comics generation]({{ orig_post.url }}) series. In this article, I provide a bird-eye view on the project milestones, focusing on desiderata and anticipating some of the challenges.

## Data processing

Here is an example of a page from the comics, directly from the editor website

![](https://en.sergiobonelli.it/resizer/420/-1/false/1705395540688.jpg--tex_willer_2024____marco_ghion.jpg){:.cnt}

Pre-processing consists of extracting each panel using traditional computer vision approaches (e.g. [openCV](https://opencv.org/)). This gives us an un-labeled dataset to work with. However, since we wish to carry out narrative reconstruction, we need to extract the text

## Text extraction

While this may seem a standard optical character recognition (OCR) task, and in fact we could approach it as such, in practice we will want to fine-tune our model on the extracted text, to teach it the comics style. Technically, this would require hand-labeling thousands of of images. Instead, what we are going to do:
- Leverage recent MLLMs that exhibit strong performance on OCR tasks, surpassing traditional approaches. See for example InternVL 2.5 and Qwen2-VL. We will discuss why this is the case. For a preview, consider the following panel 

![tex willer panel](/assets/posts/tex-willer-generation-1/tex_willer_panel_ex.jpg){:.cnt : width="70%" }

A famous OCR software, [Tesseract](https://github.com/tesseract-ocr/tesseract), extracts the following
> 'BASTA COSI» KIT:\nIL SERPENTE NON E*PIU™\nIN GRADO Di MORDE-\n\nCHE ORA E*\nBELL’E PRONTO\nPER LA RESA\n\nILLUSO...\nSAM TRUSCOTT\nNON FINIRA™\n\nIMPICCATO! 4\n\n'

While the outcome looks pretty good, we do notice that the last row of the left bubble has been lost, and both the first and last row of the top right bubble have also been lost. The quality of the extracted text is however high, here, but in other cases typos are common, especially for smaller font.

We will evaluate in details both traditional OCR and modern approaches to OCR. Moreover, we will explore whether ensembling helps improving the quality of the extracted text. For this, we will need a validation set. We will create one that suits our purpose, obviously using LLMs ;)

## Text cleaning

While the above may be a sufficient strategy, given that our task is to learn the style from the text, we really want to extract as polished of a text as possible. Remember, garbage in, garbage out. We will aim to fine-tune a MLLM on a small curated dataset (~few hundred observations) to further enhance the labeling pipeline. 

Again, from the output above (and having already seen the performance of MLLM for OCR), it may not be as crucial. But it's good learning opportunity to train these models in such a data-limiter scenario.

## Narrative reconstruction

Time to fine-tune another language model! Here we want to carry out self-supervised learning to train a LLM to generate stories in the style of the comics at hand. This is necessary for a few reasons:
- It is unlikely that the training set has any coverage of this
- The text is in italian, and the expressions used are quite particular
- We want to learn the style of the different characters (there are very interesting dynamics there). 
- We want to capture the main themes of the comics.

Learning characters' speech style may require us to identify who is talking. This would affect the data labeling step above

---

---
Wow, that was a long overview. And we are only barely half way! Stay tuned for the second part of the overview, and upcoming tutorial and articles in these series

\- Guglielmo