# variegation

# variegation
9-2-15 Joel Mathew Swenson, LBL.  Code was adopted for my purposes from many different sources and using the macro recorder.
Run using Fiji by first opening a single collage (discussed below) and then Plugins, Macros, Run or Install
Ran using Fiji 2.0.0-rc-31/1.49v; Java 1.6.0_65 [64-bit]

This script outputs 3 measurements per eye in the following order: 1. Area of segmented eye, 
2.  area of eye + black background, 3.  portion of eye counted as variegated + black background.
Use math to determine fraction of eye that is variegated. 
########Note that throughout this readme file "variegated" is used as short-hand for "color determined by the user that represents white gene product"

Input for script is a collage of all eyes of a given genotype (see suvar205^5_over_wt.tif is an example input file, suvar205^5_over_wt.tif-labeled.jpg and suvar205^5_over_wt.tifRGB0-255_0-90_0-20_var-labeled.jpg are example output files)
How I made collages:
In Fiji do:
1.
File, New, Image
Name: KV108_no-bal_SuVar205
Type: RGB
Fill with: Black
Width: 1280 pixels
Height 960 pixels
Slices: 1

2. Open all the images of a certain genotype by selecting them all in Finder and dragging them to the Fiji Menu Bar.
3. Use the "Freehand selections" tool to circle the eye, copy it, paste it into the file you created in step 1.
Note that within Fiji you can use Command+w to close the file.
4. Repeat for all eyes within a genotype making sure they don't overlap (as discussed below)
   Note that quantitation can be screwed up is there is another eye within BoxA.  BoxA is defined Xmin to Xmax and Ymin to Ymax of a given eye.
   Basically don't put two eyes too close to each other.
5. In Fiji use File, Save As, Tiff
6. Repeat for other genotypes.

Areas to target for improvement:
1. Represent segmentation more clearly in the output, 
2. Write the output automatically instead copying and pasting from the Results section
3. Automatically segment eyes (shouldn't be too hard using Weka Segmentation)
4. Enable script to run on an entire directory instead of one image at a time
5. Use PCA or Kmeans to automatically detect RGB values corresponding to variegated pixels (or other colorspace, e.g. HSB, Lab)
6. Calculate the distance (on a pixel basis) in RGB space from a "variegated" (yellow expressing) pixel (as determined in step 5) probably with different weights on different colors
NOTE THAT STEPS 5 AND 6 MAY PROVE PROBLEMATIC BECAUSE VERY VARIEGATED AND SLIGHTLY VARIEGATED MAY NOT BE PROPORTIONAL IN RGB OR ANOTHER COLORSPACE
Note: RGB Measure Plus plugin and ShapeLogic may prove useful



Set RGB values that you want to count as _variegated_
Determine values using Color inspector 3D, which is a great tool for determining how 
 		different colors are represented in different color spaces…histogram is useful within that plugin.
 NOTE YOU MAY NEED TO ADJUST VALUES BASED ON YOUR CAMERA SET-UP/GENETIC BACKGROUND (of your flies, not you)
 Special note if you don't use RGB colorspace: Color Threshold appears to have some bugs so be careful

Rmin=0;
Rmax=255;
Gmin=0;
Gmax=90;
Bmin=0;
Bmax=20;
(0-255, 0-90, 0-20) used for Heterochromatin paper (Working title and author information are below)
The composition and organization of Drosophila heterochromatin are heterogeneous and dynamic, Joel M. Swenson1,†, Serafin U. Colmenares1,†, Amy R. Strom1,2, Sylvain V. Costes1, Gary H. Karpen1,2,*
 1Division of Biological Systems and Engineering, Lawrence Berkeley National Laboratory, Berkeley, CA 94720, USA
 2Department of Molecular and Cell Biology, University of California, Berkeley, Berkeley, CA 94720, USA
 †These authors contributed equally to the paper
 *Correspondence for paper: karpen@fruitfly.org (G.H.K.)


