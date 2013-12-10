Scheme-Project-2013-csc151
==========================

By utilizing GIMP + Mediascript + Scheme, I (along with my partners) created a program that churns out 1000 unique images. Although these images aren't representational, their basic theme exudes a sense of depth and perception in deep space, overlaid with retro shape and line sequences - the shapes and lines utilize an accented analogic color scheme.

More details are explained in our design and technique statements below:

Part 1:

Design Statement 

Our drawings, image-series, showcase our group’s utilization of a variety of artistic design elements. At the core, these drawings explore the effect of color relations, motion, and depth on the viewer’s eye.

The picture plane of image-series can be easily separated into two categories: negative and positive space. The negative space of image-series can potentially consist of a variety of sizes and spacings of small white or black circles, creating a slight sense of disorganization. This variety of dots combined with the unified black or white backdrop combines to make a subtle yet interesting negative space. If the dots are black, the backdrop is white, but if the dots are white, the backdrop is black. These variations add a completely different way of looking at the image(s). The positive space is created by four straight colored lines and two arrays of circle(s) and/or triangle(s); this positive space is almost entirely created along the top-left to bottom-right diagonal, with a greater amount of positive space being created towards the bottom right of the drawing. This leaves the bottom-left and top-right spaces of the drawing filled with negative space. The result of these clearly defined regions is that the viewer’s eyes will naturally drift from the top-left down to the bottom right (or vice versa) due to the natural pull of the positive space.

The natural pull that is created via the contrast of positive and negative space can also be understood in terms of lines, depth, and motion. Image-series consists of four clearly defined lines, each of which serves to interrupt the very white/black background. Thus, these four lines each draw the attention of the viewer due to their role in emphasizing positive space and separating negative spaces. Three of these lines (L1, L2, L3) are widely separated at the bottom-right of the picture plane, but join together at the top-left of the picture plane to form the fourth line (OL). At this point of union there is a supernova—a procedure used to make the transition between lines more interesting. The result of these lines all sharing a point of origin is an illusion of depth, as it appears that these three lines are moving farther into the picture, only to merge into a supernova and reappear as one singular line.  The shapes that make up the space between these three converging lines create a feeling of motion as well as depth. These circles and/or triangles progressively, almost rhythmically, scale down as they climb towards the top-left edge of the picture plane, but the overlapping nature of the shapes makes it look as if they are moving into the picture plane towards a point of origin (or moving away from that origin).

The colors of the four lines that make up the drawing frame are dependent on complementary and analogous schemes. The OL and L2 are complements of each other. L2, L1, and L3 are pretty close to analogous to each other, with L1 corresponding to the color that is 36° counter-clockwise of the middle line’s color on the color wheel, while L3’s color corresponds to the color that is located 36° clockwise of the middle line’s color. The color of the shapes is determined by finding the color that is 90° degrees clockwise from the OL’s color, while the color of the supernova is the color that is 270° from the OL’s color.  The point of this color scheme is to get the viewer thinking, and because we think the idea is pretty cool.   

Part 2:

Technique Statement 


For the background of the image, we’ll use image-compute! to provide either a slight blend that creates a mostly black background with white, or a blend that transitions from a slight white to a mostly black background.. This will be our first technique. Three different procedures will be used to create stars:  each will make use of manipulated lists. We’ll include a modulo function that uses the image height (since the list causes the stars to be developed vertically), so that the stars repeat across the image. Since the image will be scaled, we can be sure that the number of stars will remain constant. As we will be including three different sizes of stars, we will have three different lists(S1, S2 and S3) being rendered in the background. Now, each star list will be patterned differently - S1 will be based on sine, S2 on cosine and S3 on an exponential function. Although initially we focused on mapping our formations in more linear fashion, we figured that would take a sense of depth away - the sine, cosine and exponent functions create more interesting images. Every star in the image will be colored white. This will be our second technique.
The four lines in the foreground will be built using turtles - and these will incorporate our third technique. The origin line (OL) will be tilted at 45 degrees and will be drawn at a length of one tenth of the image’s diagonal. It will use a thicker brush (scale factor 10 for an image of size 500 x 500); the other three lines will originate at the point where OL ends, the first line will continue in OL’s trajectory (L1: at the same 45 degree angle), whereas one will be tilted at 31 degrees (L2), and the other at 72 degrees (L3). Angles were shifted by a few degrees since we had to figure out the optimum path for our shape sequences to follow. All four lines will utilize the accented analogic color scheme - the OL’s color will differ based on n, and L1 will be OL’s complement, and L2 and L3 will be +/- 30 degrees the color of L1. We will use the HSV system to represent colors as they are identified on the color wheel. This will be our third technique. 

We will use turtles and basic brushes to draw our chained circles and triangles. These series of circles/triangles will be placed in the negative space between L2 and L1, and L1 and L3. By using for-each, we will allow turtle procedures to create smaller and smaller circles (or triangles, as they approach the OL). Since, the drawing will be scaled every time, we will have a set number of shapes approaching OL (regardless of n). In our previous statement, we wanted to color these shapes as either dark-grey or white, but we found that it would be more interesting if the shapes were colored - 90 degrees of OL (one of the color quads).

We have decided to vary our images by making use of individual digits given in n. Since n, at most, can have a three-digit number, each digit (unit, ten, hundreds) will determine a different aspect of our image. This way, we’ll need to alter three different aspects, each a total number of 10 times. We will create a custom procedure that will (by using modulo and division by 10), split up n into different digits. Each digit then will be used in three places: Variation in OL’s color, variation in star formation, and variation in shapes. For the OL color, since the procedure will intake an input from 0-9, we will chop the color-wheel into 10 parts. Each increment will represent 36 degrees. For star formation, the drawing will differ according to the n  given in image series; n will dictate whether S1, S2, S3 or all three appear (and the obvious two list permutations like S1, S2 and S1,S3 and S2, S3). Depending on n, the shape procedure will either create circles between L1 and L3, triangles between L1 and L3, circles between L1 and L2, triangles between L1 and L2 (or interchange one stream with triangles, vice versa). Since our background will change from predominantly white to black if n  > 4 , two possibilities  are repeated (Since a different background constitutes a unique image). 

For instance, let’s say 457 is entered as n. The unit digit will be chopped off and fed into the shape-drawing turtle procedure, the ten digit to will be entered into the line-drawing function and the hundred digit into the star-formation procedure .The color with which OL will be drawn will be 5 * 36 = 180 (green). This will also in turn then vary L1, L2 and L3. Four will then vary the star-formation spacing and seven will be one of the ten possibilities that the shape-drawing procedure will churn out.

We are also utilizing a gimp procedure called ‘plug-in-nova’ that creates a glowing supernova with a defined radius and position. The color for out supernova will rely on one of the unused color quads (+ 90 degree of OL). We’re using it to mark our convergence (or divergence; depends on how you look at it!) point (it also helps in smoothing the transition out!).
Since it is virtually impossible to scale turtle drawings, our final images won’t work for differing aspect ratios. Only when width = height will our images retain a sense of scalability. However, our non-turtle drawings do focus on being accommodating for other aspect ratios anyway. In addition, since brushes can’t scale well, we included a conditional that checks the the average image dimensions ((width+height)/2) and sees whether they’re less than 500 (and if they are, then use the most basic unit ratios e.g 1,2,3 or 1, 3, 5).  We use the same method for scaling our stars which, similarly, can’t scale below 1. 
