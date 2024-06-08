---
layout: about 
title: About
permalink: /about/
subtitle: <h1><strong>About me</strong></h1>
nav: true

profile:
  align: right 
  image: propic-collodio-bw.jpg
  image_circular: false # crops the image to make it circular
  more_info: >

---
I am a student at the end of my Master’s degree in Computer Science at the
University of Milano-Bicocca with expected graduation in October 2024 with top
marks. Currently, under the supervision of Prof. Simone Melzi, I am working on
my thesis investigating the spatial behavior and improving the faithfulness of
Diffusion Models (DMs). My journey through this program has solidified my
passion for academic research and my desire to contribute to the field of
Generative Image Synthesis.

I am passionate about computer vision, signal processing and deep learning,
which have been the main specialization areas of my degrees and internships.
During my undergraduate studies, I had the opportunity to enter the world of
academic research while also working as a Teaching Assistant, these experiences
paired with my enthusiasm for Open Source spiked my interest to continue with an
academic career as a researcher. I also had the opportunity to present one of my
works in a workshop at the annual Italian conference on artificial intelligence,
this was one of the most formative experiences of my entire academic career up
to now and made me realize how important it is to participate, discuss and
contribute in the research community.

During the two years of my Master’s program, I held the role of chairman of the
association promoting open source in my university. Together with my colleagues,
I organized numerous events, including the annual Linux Day, which attracted
over 400 participants. This experience not only reinforced my commitment to open
source and knowledge sharing but also gave me the skills to plan and execute
large-scale conferences.


## **Past Research Experience**
I focused my Bachelor's on studying the theoretical and practical aspects of
Signal and Image Processing. At the time I was interested in working with
spectrograms in time-frequency analysis, and this led me to explore the task of
speech recognition during my Bachelor's thesis. This work aimed to investigate
how temporal aggregation affects the performance of deep learning models in the
speaker verification task. The findings of my thesis were later published in a
paper presented at ICEE Berlin 2022 [[1]](https://ieeexplore.ieee.org/document/9937132).

I later followed my studies with a Master's degree in which I moved towards the
fields of Computer Vision and Machine Learning. During this time, I won a
research grant under Prof. Francesca Gasparini to develop a novel data analysis
framework in a categorical and multidimensional setting. The results of this
work were published [[2]](https://ceur-ws.org/Vol-3623/AIxAS_2023_paper_10.pdf)
and presented by me at the [AIxAS 2023 workshop](http://aixas.it/).
Furthermore, this work was later selected for an extension and publication in
the [Journal "Intelligenza
Artificiale"](https://www.iospress.com/catalog/journals/intelligenza-artificiale)
and as of writing this, the manuscript has been accepted and it is now waiting
to be published in the next issue.

Although in different fields, thanks to the projects I have been involved in
during my degrees I have gained practical experience with the world of academic
research. These experiences spiked my interest in the research world leading me
to pursue my studies with a PhD.

## **Current Research**
I am fascinated by the field of Generative Image Synthesis. I find the concept
of creating images out of nothing but a thought to be incredible. I began
working in this field during my Master's thesis with the aim to explore how
spatial information is constructed during the synthesis of an image in a
diffusion pipeline.

My interest in the field of Generative Image Synthesis has drawn me toward two
main research questions:

1. **The initial seed:** how does the initial noise affect the spatial
   composition of the generated image?
2. **Spatial conditioning:** where and how is the spatial information encoded in
   the model? How can we control it?

I started working on Diffusion Models during my Master's thesis with Professor
Simone Melzi. I first began by investigating the topic of conceptual and spatial
blending with DMs. This initial work allowed me to gain familiarity with DMs
and, an understanding of their implementation and mathematical principles.
Furthermore, the findings of this research allowed me to gain valuable insights
into how semantics is spatially constructed during the synthesis of an image.
The results of this initial work were submitted and accepted at the 
[EKAPI 2024 workshop](https://sites.google.com/unical.it/ekapi-2024/home).
 This work is currently in press, you can check out some of the results in my
blog post
[Blending Diffusion Models](https://lorenzo.olearo.com/blog/2024/blending-diffusion-models).

### **The initial seed**
The initial seed Diffusion Models (DMs) were first introduced in 2015 by
Sohl-Dickstein et al. [[3]](https://arxiv.org/abs/1503.03585) but only in 2020
with the work of Ho et al. [[4]](https://arxiv.org/abs/2006.11239) their potential
in high-resolution image synthesis was fully realized. DMs are a class of
generative models inspired by non- equilibrium statistical physics, the main
idea behind these models is to systematically and slowly destroy the structure
in the data through an iterative forward diffusion process until pure noise is
obtained, this process is modeled as Markov chain that gradually adds noise to
the data. To then reverse this process, a parameterized Markov chain trained
using vari- ational inference is learned. This parametrization can be greatly
simplified using sampling chains with conditional Gaussian when the diffusion
process is modeled with small amounts of Gaussian noise.

Despite the numerous advancements since their introduction, one of the key open
issues with DMs is their unpredictable behavior due to their reliance on the
Markov chain to reverse the diffusion process. This makes the reverse process
particularly sensitive to the initial noise from which the image is generated:
two identical models with the same conditioning signal will generate
considerably different results when starting with different initial noises.
Having such an unpredictable behavior, users end up running multiple times the
same model with the same conditioning signal until satisfied with its spatial
content. This poses a serious issue especially when considering the huge
computational and environmental impact of these models. A more predictable and
controllable behavior is needed to make these models more sustainable and
scalable in a real-world scenario.

While working on blending DMs for my latest publication, I found that the
encoding stage of the UNet model has some interesting properties that could be
exploited to reduce the variability of the generated images. I have found that
conditioning at different levels changes which features are represented in the
final image, moreover, from initial experiments I suspect that the shape is
entirely defined in the encoding part of the model while the details related to
the semantics of the prompt are added in the decoding part. I find this behavior
particularly interesting and plan to explore it further during my PhD as I
believe this could give rise to a new and better way to condition DMs.

Some variability in the image generation is still desirable as the user cannot
be expected to provide the entire description of every aspect of the image he
has in mind, the model should still be able to add some “unexpected variations”
during the synthesis. What I plan to explore is a new and more controllable
method to condition the generation, not removing any aspect of stochasticity in
the synthesis but rather understanding where the different 2elements of the
semantic are constructed during the generation.

### **Spatial conditioning**
My interest in making DMs more controllable led me to the
question of how to control the spatial composition of the final image. While
semantic conditioning has been widely explored, spatial conditioning and its
relationship with the semantic content of the generated image is an open
challenge. The advancements in this field are limited and extremely recent, most
of the work in the area has been presented during the last year at top
conferences in computer vision.

Many approaches have been proposed with different levels of success, I find the
method proposed by Zhang et al. in ControlNet
[[5]](https://arxiv.org/abs/2302.05543) to be one of the smartest and most
elegant up to date. Instead of adding additional channels to the diffusion
process like in [[6]](https://arxiv.org/abs/2211.14305) and the StabilityAI
depth-to-image Stable Diffusion model [[7]](https://arxiv.org/abs/2112.10752),
the authors proposed to lock the weights of the production ready diffusion model
and train a copy of its encoding blocks on a new conditioning task, the two
models are then connected with zero-convolution. The authors show that this
approach allows the control of Stable Diffusion with various conditioning
inputs, including Canny edges, Hough lines, user scribbles, human key points,
segmentation maps, shape normals, and depths.

This approach is particularly efficient and has been greatly adopted by the
image synthesis community. Furthermore, the model used to condition the
generation is also way cheaper to train compared to the previous approaches.
Comparing it in depth-to-image task with the Stability AI model mentioned
earlier trained with a large-scale NVIDIA A100 cluster for thousands of hours,
ControlNet was trained for 5 days on a single consumer-grade NVIDIA 3090Ti GPU.

I think the approach proposed by ControlNet reinforces my previous hypothesis
that the shape is defined in the encoding part of the UNet model, this is one of
the arguments that I plan to clarify during my PhD. If this is true, it could
lead to a new way to control the spatial composition of an image, for example,
assume we are interested in generating human subjects in different poses, the
pose of the subject could be controlled by injecting a pose embedding in the
encoding layers of the UNet while its details and characteristics could be
controlled by the prompt embedding injected in the decoding blocks.

## **Future Plans**
My career aspiration is to become a researcher and possibly a professor in the
field of Generative Image Synthesis, this choice is driven by my experience as a
teaching assistant during my Master's degree and my passion for sharing
knowledge with others. Pursuing a PhD will allow me to continue my research and
studies while gaining further teaching experience.
