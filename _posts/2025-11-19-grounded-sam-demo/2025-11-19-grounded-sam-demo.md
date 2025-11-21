---
title: Grounded SAM demo
date: 2025-11-19
tags:
- methods
- python
- cv
---

# High throughput image segmentation

I put together a minimal demo to use [Grounded SAM](https://github.com/IDEA-Research/Grounded-Segment-Anything): Grounding DINO text prompts + Segment Anything Model. This enables rapid automated extraction of regions of interest from images, e.g. to segment biological specimen. The demo contains instructions for installation and a jupyter notebook, all hosted on github - feel free to give it a try:

<div class="image-thumb">
    <a href="https://github.com/mluerig/demo-grounded-sam" target="_blank">
        <img src="https://raw.githubusercontent.com/mluerig/demo-grounded-sam/main/sam3-animation.gif" style="width: 80%;">
    > Animation of the SAM3 textprompt - the principle is the same for GroundedSAM < </a>
</div>

If you don't use a GPU the model is pretty slow (up to a minute per image, or even more), otherwise it runs pretty fast, even on small or mid-size GPUs. I provided some test images of butterflies, which are highly standardized, but it should work well on unstandardized images, e.g., from iNaturalist.   