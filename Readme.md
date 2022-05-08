## What is this
Jpegtran extension for lossless pixelization.
The goal of this repository is providing blur operation without loss.

## What is Jpegtran
Jpegtran is a command line program which can exetute the following operations to JPEG image without loss.
- Crop
- Rotate (90,180,270 degrees)
- Flip (horizontal,vertical)
- To Grayscale

It is a part of the IJG(Independet JPEG Group) code.

## File list
- [ChangesIJG.md](ChangesIJG.md)  
This file describes the changes from the original IJG code.
- [License.md](License.md)  
License terms for this codes

## How to build
Execute makefile.
Attached makefile is for cygwin with mingw64.
Modify it to your development environment.

## Usage
The general options are same as Jpegtran.  
The following options is not compiled.
- `-progressive`
- `-arithmetic`
- `-scan`

Pixelization option is exclusive of other transfromation option, crop, rotate, flip....

Extension opition format is below.  
`-pixelize (width)x(height)+(posx)+(posy)@(blkX)@(blkY)[a]`  
This option can be specified multiple times, maximum 8.
It can be changed by modify line 58 in [jpegtran.c](jpegtran.c).

Example  
- `-pixelize 640x480+0+0@4@4`  
width : 640  
height : 480  
position : (0,0)  
pixelized block width : (MCU x 4)  
pixelized block height : (MCU x 4)  
Align mode : off  
- `-pixelize 320x240+192+256@1@2`  
width : 320  
height : 240  
position : (192,256)  
pixelized block width : (MCU x 1)  
pixelized block height : (MCU x 2)  
Align mode : on  
- `-pixelize 512x384-64-48@0`  
width : 512  
height : 384  
position : (64,48) (from lower right corner)  
pixelized block width : block  
pixelized block height : block  
Align mode : don't care  
- `-pixelize 640x480+0+0@4@4 -pixelize 640x480+0+480@8@8`  
2 parts for pixelization area are specified.
