# Thermal Image Analysis #
I used this project to practice with some image analysis. I have not worked with images for a couple of years so I decided to revisit packages Python uses for image analysis. I chose to use scikit-image based on the documentation and compatability with Anaconda. 

As well as keeping up on experience, I also was practicing as I was going to need to identifiy objects in thermal images for my summer internship at Johnsonville. That is why I chose to use this thermal image of a pig:
![](images/original.png)


After researching online I chose to use a few different methods. Here are the links to articles I found on these. <br>
**Thresholding:** https://scikit-image.org/docs/stable/auto_examples/applications/plot_thresholding.html <br>
**Canny Edge Detection:** https://datacarpentry.org/image-processing/08-edge-detection/ <br>
**Various Methods Including Watershed Transform:** https://scikit-image.org/docs/dev/user_guide/tutorial_segmentation.html

Here are the results of each method:
### Thresholding ###
This method consisted of turning the image to greyscale. Normally you would look at a histogram of the grayscale values and select a value that is the cutoff. The values on one side of the cutoff would be made white and the rest would be black essentially creating a mask. There are various functions in Scikit-Image that do this automatically so I did not select a value.

![](images/threshold.png)

After seeing them all I selected the two best methods and compared those.
![](images/threshold2.png)

### Canny Edge Detection ###
Canny Edge detection involves applying a gaussian blur to the image to make it noisy. It then uses a formula to identify where the edges of the image are. There are different parameters to play with, one of the important ones being sigma which I changed as you can see in the image below.<br>
![](images/canny.png) <br>
Now this worked pretty well in finding some of the edges but unfortunately I was not able to fill in the inside of the edges since they are not all connected. This means I wasn't able to make a mask to identify the image.<br>

### Watershed ###
This method involves first creating an elevation map out of the image. This is what that looks like:<br>
![](images/elevationmap.png) <br>
Then you need to find markers of grayscale value to input into the watershed function from a histogram.<br> 
![](images/histogram.png)<br>
And finally you can create a watershed.<br>
![](images/watershed.png)<br>

### Comparison of Methods ###
Out of all the methods it appears like the watershed method correctly selected the majority of the pig in the image. <br>
![](images/endcomparison.png)
