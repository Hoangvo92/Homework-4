# Homework-4

First 5 days, download the zip file from Blackboard, unzip, could not run on Visual Studio.
  -add independencies into the VC properties: window-only-stuff, new Eigen3.7 (ask TA about the Eigen issue)
      The link to download Eiga 3.7: http://eigen.tuxfamily.org/index.php?title=Main_Page
  -replace the CPP files and header files with files in /include and /src
  -Run and could have the image of 1 big sphere and 2 small spheres. (Beginning.png)
  
 Before doing the project, install many packages: Freeglut, GLEW, GFLW, glm
 Libraries: GLEW, Zlib, libPng
On November 19, try to solve the first problem:
"Problem 1 (25 points). The ray tracer currently only can draw spheres. Add at least one more shapes. Potential options include other primitives, smooth surfaces with closed form equations f (_x) = 0, etc.; remember that all you need to add a shape to your ray tracer are methods for ray intersection and computing normals."
 -I choose to add in a box or a cube. The files cube.h and cube.cpp contain class cube and method of ray intersection.
 -I used the algorithm in this link: https://www.scratchapixel.com/lessons/3d-basic-rendering/minimal-ray-tracer-rendering-simple-shapes/ray-box-intersection
     + creating min and max points as the boundary of a box: bounds[0]
     + computing tmin in 3 different scenarios. Unlike sphere, a cube box is created by 6 flat surfaces.
     +compute tnear or tmin in situation of Ox, Oy, or Oz axis.
 -In the link above, there are instructions and explanation about ray-intersection in box. 
 -to compute normal vector at the hit points, I used algorithm in this link: https://blog.johnnovak.net/2016/10/22/the-nim-raytracer-project-part-4-calculating-box-normals/
 -Add two cubes in the main.cpp
 -run the code and could have the image including: 3 spheres in Starter_code, and 2 cubes. (Step1.png)
 Try to solve the second problem:
