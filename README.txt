///////////////////////////////////////////////////////////////////

  GN-PolyBoolean - README

///////////////////////////////////////////////////////////////////



1) Introduction
---------------

This project provides a C++ implementation of 2D Boolean operations,
 capable of computing intersection, union and difference between 
two non-self-intersecting complex polygons (supporting both double-ring 
and single-ring structures). The implementation handles degenerate 
intersection cases including multiple coincident vertices and overlapping 
edges.


2) Compiling
------------

In the current folder, hold down the Shift key and right-click with the mouse, 
then select "Open in Terminal" (Powershell)



3) Executing
------------

In the terminal interface, enter the command

  .\myBoolean.exe xx-xx-xx.txt

xx-xx-xx.txt is the input file, where each file contains two shapes. The Boolean 
operation type can be specified by modifying the filename.output.txt is the 
output file.

.\myBoolean.exe 0-9-15.txt


4) File Format
--------------


xx-xx-xx.txt represents the filename, which must strictly adhere to the following 
naming convention:

The filename consists of three parts:
- First part: Specifies the Boolean operation type. Only four values are allowed:
  0 - Intersection
  1 - Union
  2 - A minus B
  3 - B minus A
- Second part: The number of vertices in Polygon A.
- Third part: The number of vertices in Polygon B.


5) Admitted Input
-----------------


- The vertex count must include both the start and end points. For example, If Polygon
   A is a triangle, its vertex count should be 4. If Polygon B is a square, its vertex count
   should be 5.
   Example: To perform an intersection operation on two rectangles, the filename should
   be 0-5-5.txt, and the command in the terminal should be .\myBoolean.exe 0-5-5.txt.
- The content of the .txt file must strictly follow this format: xx, xx (Note: There should be
   a comma followed by a space between the two numbers.)
- Data input in the .txt file must follow:
   Outer rings: Vertices must be input in counter-clockwise (CCW) order.
   Inner rings (holes): Vertices must be input in clockwise (CW) order.

For example: The following 14 lines describe two shapes for Boolean operations:

0, 0
4, 0
4, 4
0, 4
0, 0
1, 1
2, 3
3, 1
1, 1
2, 2
6, 2
6, 6
2, 6
2, 2


The input polygons allow the following characteristics:
- The vertices of outer rings must be ordered counter-clockwise (CCW). The vertices of inner
   rings (holes) must be ordered clockwise (CW).
- Components can be nested (polygons with holes).
- The two input polygons are allowed to have degenerate intersections (vertex on edge, 
   overlapping edges, etc.) with each other.

6) Robustness
-------------

The implementation is based on C++ floating point numbers with
double precision . The EPSILON parameter
(set to 0.000001) is used as a tolerance for equality checks,
and two numbers are considered equal if their difference is less
than EPSILON.






