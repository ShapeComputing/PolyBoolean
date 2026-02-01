///////////////////////////////////////////////////////////////////

  GN-PolyBoolean - README

///////////////////////////////////////////////////////////////////


1. Introduction
---------------

This project provides a C++ implementation of 2D Polygonal Boolean operations,
 capable of computing intersection, union and difference between 
two non-self-intersecting  polygons (supporting both convex and concave polygons, including those with holes
). The implementation handles all kinds of degenerate 
intersection cases ,including multiple coincident vertices and overlapping 
edges.


2. Compiling
------------

In the current folder, hold down the Shift key and right-click with the mouse, 
then select "Open in Terminal" (Powershell)


3. Executing
------------

In the terminal interface, enter the command

  .\GN-PolyBool.exe x-xx-xx.txt

x-xx-xx.txt is the input file to specify the boolean operation type and two polygons. The result is saved in the " output.txt".

For exmple, to operate the input file of 0-9-15 

 .\GN-PolyBool.exe 0-9-15.txt


4.File Format
--------------
x-xx-xx.txt represents the filename, which must strictly adhere to the following 
naming rules:

The filename consists of three parts:

- The First part: Specifies the Boolean operation type. Only four values are allowed:
  0 - Intersection
  1 - Union
  2 - A minus B
  3 - B minus A

- The second part : The number of vertices in Polygon A. 

- The third part: The number of vertices in Polygon B.

Notes: 
The count of vertexes of  a polygon here is the real count +1 (The start vertex and the end vertex are  the same to get a closed loop). For example, to perform an intersection operation on two rectangles, the filename should  be "0-5-5.txt", and the command in the terminal should be .\GN-PolyBool.exe 0-5-5.txt

5. Data  Format
------------
1) Two coordinates of a point are separated by a comma. 
2) The order of the vertexes in a polygon:   Outer rings: Vertices must be input in counter-clockwise (CCW) order; Inner rings (holes): Vertices must be input in clockwise (CW) order.
3) the number of vertex coordinate rows should equal the number of vertices plus one,for each polygon.
 For example,the data in the file "2-5-15" indicates:
  Polygon A is a quadrilateral (4-sided polygon). Its start point and end point are the same 
27, -6
45, -6
45, 64
27, 64 
27, -6
Polygon B is a 14-edge polygon, with the last 15 rows representing its vertex coordinates. The start point and end point coordinates are identical, forming a closed loop.
0, 0
50, 0
50, 10
10, 10
10, 50
40, 50
40, 30
30, 30
30, 40
20, 40
20, 20
50, 20
50, 60
0, 60
0, 0

6. Sample test 
------------
following the steps ,to run the sample test
1）In the current folder, hold down the Shift key and right-click with the mouse, 
then select "Open in Terminal" (Powershell)
2）enter the responding command for each file，examples :   
    .\GN-PolyBool.exe 0-9-15.txt

    .\GN-PolyBool.exe 0-5-15.txt

    .\GN-PolyBool.exe 1-9-15.txt

    .\GN-PolyBool.exe 1-5-15.txt

    .\GN-PolyBool.exe 2-5-15.txt

    .\GN-PolyBool.exe 3-5-15.txt

You can also modify the first digit in the test filename with 0, 1, 2, or 3 to obtain different  Boolean operations, the same as the files of 
 0-5-15.txt
 1-5-15.txt
 2-5-15.txt
 3-5-15.txt

The file"results" shows the correct results of  sample test.

7. Robustness
-------------

The implementation is based on C++ floating point numbers with
double precision . The EPSILON parameter
(set to 0.000001) is used as a tolerance for equality checks,
and two numbers are considered equal if their difference is less
than EPSILON.
