# Style Transfer Analysis

DSC160 Data Science and the Arts - Midterm Project Repository - Spring 2020

Project Team Members: 
- Nikolas Racelis-Russell, nracelis@ucsd.edu

## Abstract

Style transfer is a computer vision optimization problem in which a neural network recomposes an image in the style of another image. This means that one could re-imagine a famous historic picture, or even a meme - in the style of a famous artist's work like Van Gogh's "Starry Night." In fact, this Van Gogh style transfer is the example from which this project took its inspiration from.

This project used architectural art from [Zdzislaw's Beksinski's wiki art page](https://www.wikiart.org/en/zdislav-beksinski), specifically [untitled-14](https://www.wikiart.org/en/zdislav-beksinski/untitled-14). The goal was to transfer some of Beksinski's hellscapes to real life, and observe how that would manifest. 

This project closely followed the methods from [Leon A. Gatys, *et al.*'s paper, A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf), as well as used code from [Google Collab's Neural Style Transfer with tf.keras](https://colab.research.google.com/github/tensorflow/models/blob/master/research/nst_blogpost/4_Neural_Style_Transfer_with_Eager_Execution.ipynb#scrollTo=aDyGj8DmXCJI) to create and run the model using the [VGG19 CNN](https://keras.io/api/applications/vgg/#vgg19-function).

For the analysis aspect of the project, the content image that was recomposed using style transfer was measured for Hue, Saturation, Value (HSV) and [Pleasure, Dominance, and Arousal](https://dl.acm.org/doi/pdf/10.1145/1873951.1873965) (inspired from looking at [Group-14's project](https://github.com/ucsd-dsc-arts/dsc160-midterm-group13)).


## Data

A Zdzislaw Beksinski's [untitled-14 painting](https://www.wikiart.org/en/zdislav-beksinski/untitled-14) was scraped from wikiart for the style image, whilst another architectural image of the Petronas Towers in Dubai, was taken from google as the content image.


## Code
- Style Transfer was performed in ["Style Transfer Model (VGG19).ipynb"](https://github.com/nikolettuce/dsc160_midterm/blob/master/Style%20Transfer%20Model%20(VGG19).ipynb)
- Code for Analysis was performed in "Style Transfer Analysis.ipynb"
  - Pleasure, Arousal, and Dominance measures.
  - HSV measures

## Results
### Style Transfer Results
- After 1000 iterations, the style transfer has worked observably well, as the realistic image has been shifted to something definitely resembling Beksinski's works.
![model_array](https://github.com/nikolettuce/dsc160_midterm/blob/master/markdown_images/model_array.png)
![input_style_output](https://github.com/nikolettuce/dsc160_midterm/blob/master/markdown_images/content_style_output.jpg)
- Here, the output image can be seen incorporating the sort of web-like architecture that Beksinski had created in his painting, albeit on a much less detailed level. The output image has also created space where it used to be negative - particularly above the bridge structure.
### Analysis
- Original, HSV Values plotted:
![hsv_plotted](https://github.com/nikolettuce/dsc160_midterm/blob/master/markdown_images/chrome_pEfi9vni9c.jpg)
![hsv_plotted_data](https://github.com/nikolettuce/dsc160_midterm/blob/master/markdown_images/hsv.png)
   - In the Hue channel, the predominantly blue content image was changed to a mixture between the orange from the style image, and slight amounts of blue from the original content image.
   - In the Saturation channel, we can see that the output image's variation in color intensity was lowered from the content image and brought to have a closer spread, indicated by the lack of large dark blue/black spots that were in the content and style images.
   - Value Channel seems to have just been brought closer to the style image, since the content image was bright initially.
 
- Pleasure, Arousal, and Dominance plotted:
 ![pad](https://github.com/nikolettuce/dsc160_midterm/blob/master/markdown_images/pad.png)
  - Here, what stood out to me was that the Beksinski painting had a higher Pleasure rating than the Petronas towers, and that they all had similar arousal ratings. 
  - However, the dominance rating made more sense, as subjectively within my own head, the style image is more dominant than the content image, resulting in a more 'dominant' output image.
## Discussion
The results given by the style transfer were subjectively satisfactory, however the metrics used to evaluate how the original content image was change was a bit perplexing. Given that style transfer is an optimization problem between minimizing both style and content loss. Intuitively, I had believed that this would mean for values like hue, saturation, and value - that the output image would be somewhere in between the values of the content and style images. However, the output's values for hue and brightness were much more similar to the style image's values than the content image's values. A similar phenomena could be observed in the pleasure, arousal, and dominance factors, however this is attributed to the fact they're derived from the HSV values.

This approach is different than the traditional way of imitating an artists style because whilst someone could impersonate an artist's work with their own eye, this approach is based on statistics and neural networks. Additionally, for the analysis portion, it's different because of how empirical a traditional comparisons would be. Whereas by measuring the HSV values, it's an objective statistic. Additionally, it's also possible to compare a large amount of images at once, whilst a subjective method would take way longer to compare.

I think if Beksinski saw this, I'm honestly not sure what he would say (he didn't even like to name his own paintings because he didn't want the name to misconstrue any meaning, which he believed was different for each person!). But perhaps it could also be seen as an extension of his work, as his art was surrealist; whereas the output image from the style transfer was initially something in real life. I believe style transfer could be a way to reimagine images through the lense of artists that are no longer with us, though whether they would agree is debatable.

This work could be expanded upon by attempting to use multiple style images, though I'm not quite sure what the implications for that would be. Additionally, it would be interesting to see how using some of Beksinski's paintings with different styles would affect the style transfer (i.e using some of his more minimalist line work paintings as the content image and transferring them to be more detailed).

## Technical Notes and Dependencies
- Tensorflow

## Reference
- [Leon A. Gatys, *et al.*'s paper, A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf)
- [Google Collab's Neural Style Transfer with tf.keras](https://colab.research.google.com/github/tensorflow/models/blob/master/research/nst_blogpost/4_Neural_Style_Transfer_with_Eager_Execution.ipynb#scrollTo=aDyGj8DmXCJI)
- [Pleasure, Dominance, and Arousal](https://dl.acm.org/doi/pdf/10.1145/1873951.1873965)
