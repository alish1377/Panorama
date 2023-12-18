# Panorama
In this work, a Panorama of a simple video is created from scratch with Python and OpenCV. In each 20 frames, I got one and added it to the last Panorama frame
## Workflow
* A: Use the Sift algorithm to find key points of each frame
* B: Use the BFMatcher with the knnMatch to find the corresponding points of 2 frames
* C: Check the uniqueness condition of the Homography matrix
* D: Obtain the Homography matrix with the findHomography method and the RANSAC algorithm
* E: Add the second frame to the first frame with the warpPerspective method
* F, G, H: Fill the empty pixels with the method described below
### Details of filling empty pixels(F,G,H parts)
I created a complete white mask that is dimensionally as same as the second frame. secondly, add this mask with the obtained Homography matrix and the warpPerspective method to the first frame and name the result, warped_mask. Then, detect the edges of the warped_mask using the Canny edge detector. next, in the new warped frame, fill the pixels that either are not white in the warped_mask or are lying on the edges. Finally, all black rows and columns are removed from the panorama image.
