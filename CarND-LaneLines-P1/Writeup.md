# Report
# Describe the pipeline
- Petty much straightforward:
	- Convert img to grayscale
	- Blur it
	- Run canny edge detection on that image
	- Define the region you are interested in
	- Extract edges that are in that region
	- Run Hough transform on remaining edges. This gives set of lines
	- Blend them with original image.
	Result will be image with detected lane lines on top (NB! this is true only in this example. We can detect much more than just line lines)
	
	P.S. I have a strong feeling that system must remember previous lines result. Would avoid many problematic regions. And also the notion that line renderer changes information was new to me. I always worked in a way that rendering newer changes data.


# Identify any shortcomings
  - Messed way to install the environment. Initially it was easy - I have my python installation with all necessary libs installed. Conda is mess - some libs is not in repo so you have to spend time to google how to install it.
  - Anaconda itself is very slow.
  - Github clone fo me was the problem. I think I just used to svn.
  right.
 - Trying to guess parameters is really stressing
 - Ñonstant need to restart engine is annoying
 
 In the end last two videos are hardest.

# Suggest possible improvements
 - Present Anaconda in the beginning. I messed my schedule due to that - while I was using python it was fast. Today I spent more than 8h only for configuring. The only good part is that this happens only once =)

