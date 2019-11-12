# Homework-4
#author: Hoang Vo
#Basing on the HW4-starter-code
#begin: Nov 1st, 2019
First 5 days, download the zip file from Blackboard, unzip, could not run on Visual Studio.
  -add independencies into the VC properties: window-only-stuff, new Eigen3.7 (ask TA about the Eigen issue)
      The link to download Eiga 3.7: http://eigen.tuxfamily.org/index.php?title=Main_Page
  -replace the CPP files and header files with files in /include and /src
  -Run and could have the image of 1 big sphere and 2 small spheres. (Beginning.png)
  
 Before doing the project, install many packages: Freeglut, GLEW, GFLW, glm
 Libraries: GLEW, Zlib, libPng
On November 9, 2019, try to solve the first problem:
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
 On November 10, 2019, Try to solve the second problem:
 "Problem 2 (25 points). Right now our output looks pretty boring since there is no color and all the textures are Lambertian. Add support for Phong shading as discussed in the last assignment, and make sure each shape can have its own unique colored material."
   - in Shape.h, modify the struct HitRecord: adding two variables colorS and texture
     struct HitRecord {
       Eigen::Vector3d position, normal, colorS;
       double t;
       Eigen::Vector2d texture;
       };
      the colorS will receive values of RBG color from sphere or cube.
      The texture will receive values of materials and shading.
    - in class shape, cube, and sphere in Shape.h, cube.h, and Sphere.h, adding Vector3d colorS in private section
    -When computing ray intersection in cube.cpp and Sphere.cpp, I also compute texture in HitRecord result variable. At the same time, I pass in colorS value of Shape into result for computation.
    - in Scene.cpp, the trace() handles the value of pixel in printing image
       +I borrow the idea from this public link:  https://www.scratchapixel.com/code/upload/ray-tracing-simple-shapes/simpleshapes.cpp  and https://www.scratchapixel.com/lessons/3d-basic-rendering/minimal-ray-tracer-rendering-simple-shapes/minimal-ray-tracer-rendering-spheres(it is for free use)
       "Vec3f castRay(
    const Vec3f &orig, const Vec3f &dir,
    const std::vector<std::unique_ptr<Object>> &objects)
{
    Vec3f hitColor = 0;
    const Object *hitObject = nullptr; // this is a pointer to the hit object
    float t; // this is the intersection distance from the ray origin to the hit point
    if (trace(orig, dir, objects, t, hitObject)) {
        Vec3f Phit = orig + dir * t;
        Vec3f Nhit;
        Vec2f tex;
        hitObject->getSurfaceData(Phit, Nhit, tex);
        // Use the normal and texture coordinates to shade the hit point.
        // The normal is used to compute a simple facing ratio and the texture coordinate
        // to compute a basic checker board pattern
        float scale = 4;
        float pattern = (fmodf(tex.x * scale, 1) > 0.5) ^ (fmodf(tex.y * scale, 1) > 0.5);
        hitColor = std::max(0.f, Nhit.dotProduct(-dir)) * mix(hitObject->color, hitObject->color * 0.8, pattern);
    }

    return hitColor;
} "
    +Using the solution of Phong.frag from Homework3.
    + before writing code, i used comment to mark the resemble variables in starter code: hitColor==result, hitObject==r
    +Using Ambient+ diffuse+ specular to compute the color of image
    +In the function trace(), after r has values, I perform the computation of hitcolor==result, having shading and color.
    -In main.cpp, I add variable color to input into shape. THe DoubleRand() function will generate values of Vector3d color, or I simply hard-code the values.
    
  
       
