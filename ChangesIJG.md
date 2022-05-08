## Overview
This document describes changing the IJG code.
Base version of the IJG code is **9c**. (Not latest)

The changes were made from the following three points.
- Remove unused functions and files.
- Add extension functions.


## Remove unused
### Remove unused files
The following files are removed.
- makefile, cofig files and project files for another systems  
- files for unused functions  
image reader,image writer, DCT, iDCT, command line interface...

### Remove unused functions
Modified [`jmorecfg.h`](jmorecfg.h) for removing unused functions.
Some '#define' are commented out.

## Add extension functions
### Pixelization(block)
The function make 8x8 pixelization.
The function is implemented to do_pixelize() function in [`transupp.c`](transupp.c).
The function is based on do_wipe() function.
do_wipe() clears all DCT coefficent to fill block with gray color.
do_pixelize() clears AC coefficients only, this causes 8x8 pixlization.

### Pixelization(MCU)
The function make pixelization in MCU unit.
The function is implemented to do_pixelize2() function in [`transupp.c`](transupp.c).
The function is based on do_pixelize(), block pixelization function.
do_pixelize() clears AC coefficients in a block.
In addition to that, do_pixelize2() average DC coefficinet in MCU.





