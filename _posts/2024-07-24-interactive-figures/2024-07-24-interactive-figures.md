---
title: How to make interactive figures
date: 2024-07-24
tags: 
- methods
- python
---

# Background 

Interpreting phenotypic variation presented through scientific figures is often challenging because the traits of interest are hidden behind data points. Specifically, in scatterplots or biplots of Principal Component Analysis (PCA), which can be very high-dimensional, the visual impression often remains abstract. Using pictograms in addition to data points, or adding interactive elements, can be a powerful way to increase the communicative value of a figure (especially if your study organism is as charismatic as these Junonia butterflies below). Interactive figures that show organisms are becoming increasingly feasible with the use of computer vision (automated extraction of meaningful information from images) to extract not only the phenotypic information but the relevant regions of interest (ROIs) themselves. In this post, I will show how to implement both approaches in Python, using the matplotlib and bokeh library

<div class="image-thumb">
	<a data-src="junonia_interactive_tsne.gif" data-lightbox="post" data-title="Interactive t-SNE of Junonia">
		<img>
	</a>
</div>

<div class="image-thumb">
	<a data-src="junonia_pictograms_tsne.jpg" data-lightbox="post" data-title="Pictogram-based t-SNE of Junonia">
		<img >
	</a>
</div>

## Pictogram-based figure

In this approach the goal is to plot the pictograms directly into the plot panel, which can be useful if you want to see all the variation in your dataset at once, so relationships of interest become visible, or if interactive figures are not an option (e.g., in publications). This is fairly straightforward using [matplotlib's offsetbox module](https://matplotlib.org/stable/api/offsetbox_api.html#matplotlib.offsetbox.OffsetImage). Below is an example that uses the ROIs from a scan image to demonstrate how pigmentation increases with body size in isopods — see the result below, where the pictograms are plotted at their centroid on top of the data point:

<div class="gallery-grid">
	<div class="image-thumb">
		<a data-src="scanned_image_resized.jpg" data-lightbox="post" data-title="The raw data: a scanned batch of isopods">
			<img>
		</a>
	</div>

	<div class="image-thumb">
		<a data-src="figure_isopods_pictograms.jpg" data-lightbox="post" data-title="The plot with a pictogram of each isopod plotted on top of the data points.">
			<img>
		</a>
	</div>
</div>



Reproduce the figure with the following gist and by [downloading the isopod dataset and scripts](https://osf.io/download/6u5ry/).

<div class="gist-center">
	<script src="https://gist.github.com/mluerig/b4ea5c3744c3747c76f9400e2ea8b3f1.js"></script>
</div>

## Interactive figures

The solution for producing interactive figures is a bit more involved (but not too much). Here we use [bokeh, an extremely powerful library](https://docs.bokeh.org/en/latest/docs/gallery.html) for static and interactive plots in Python. bokeh allows you to add all sorts of tools (e.g. box or lasso selection), but the most important one here  is the creation of a custom [java-based hover tool](https://docs.bokeh.org/en/latest/docs/user_guide/interaction/js_callbacks.html). This tool displays trait information and pictograms that have been extracted from the same scan image as above in a panel to the right when hovering over points on the scatter plot. The final layout, which combines the scatter plot and image display, is rendered and saved as an HTML file - give it a try by hovering over the points: 

<div class="html-center">
	<div class="html-align">
		{% include_relative figure_isopods_interactive.html %}
	</div>
</div>

Reproduce the figure with the following gist and by [downloading the isopod dataset and scripts](https://osf.io/download/6u5ry/).

<div class="gist-center">
	<script src="https://gist.github.com/mluerig/efa169be9c6580538d9ad48ce7977c8c.js"></script>
</div>
