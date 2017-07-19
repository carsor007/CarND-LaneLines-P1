# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

1.I converted the images to grayscale.

2.I applied Gaussian smoothing. The kernel size is 5.

3.I applied Canny edge detector with the following parameters.
        low threshold = 50
        high threshold = 150

4.I masked the images.

        vertices = (bottom left, (430, 310), (510, 310), bottom right)
        
5.I applied the Hough transformation with the following parameters.

       rho = 1
       theta = np.pi/180
       threshold = 10
       min line length = 40
       max line gap = 20

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by the following procedures.

1) I separated line segments to left or right lane by their slope.
   - left lane: tan(-pi/3) < slope < tan(-pi/9)
   - right lane: tan(pi/9) < slope < tan(pi/3)
   - dump: else

   

2) I calculated the slope of the left and right lanes by averaging the segments slopes categorized into them.

3) I calculated the intersection point of the each lanes and y = 320 by averaging the intersection points of the each line segments and y = 320.

    

4) I calculated the intersection point of the each lanes and the bottom line.

   

5) I drew a single line on the left and right lanes.

    

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
