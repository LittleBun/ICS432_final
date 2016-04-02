# ICS432_final
You are expected to do your own work on all homework assignments. You may (and are encouraged to) engage in general discussions with your classmates regarding the assignments, but specific details of a solution, including the solution itself, must always be your own work. (See the statement of Academic Dishonesty on the Syllabus.)

What to turn in? 

You should turn in an electronic archive (.zip, .tar., .tgz, etc.). The archive must contain a single top-level directory called ics432_project_NAME, where “NAME” is your UH username.

Assignments need to be turned in via Laulima.

What to run on? 
We will test your code on a standard multi-core Linux platform.

Raytracing Acceleration
You were hired in a company that does ray tracing, and your first assignment is to accelerate an in-house raytracer. Here is the archive: melange_v0.zip. The code is a mix of C++ and C, but mostly looks very C-ish. The archive includes a sample scene to render, and the code produces an image in ppm format called rendered.ppm. Here is the content of the archive:

% ls
melange_v0.zip
% unzip melange_v0.zip
% cd melange_v0
% ls
Makefile     compare_ppm.pl ezxml.h      
graphics.h   melange.h    scene.xml
ezxml.c      graphics.cpp main.cpp
Running the code is straightforward:

% make
% make run
Elapsed time: 132.45 sec
The code prints its elapsed time. When done, you will see file rendered.ppm in the current directory, which is a typical “reflecting spheres” image.

Your objective is to accelerate this code, using whatever means you want, while maintaining correctness.

Code versions

You must create multiple copies of the original code directory, naming each such directory melange_vX, where “X” is a version number (melange_v1, melange_v2, etc.). Each directory corresponds to one optimization attempt that is correct (i.e., it does not break the code).

It is surprisingly easy to break the code, so always keeping the last correct version if useful. Furthermore, it will make your report easier to write (“v1 did this and accelerated the code by xx%”, “v2 did this additional thing and accelerated the code by xx%”, etc.). Checking correctness entails making sure that the output is the same, e.g., looking at the picture or using the compare_ppm.pl Perl script included in the archive.

Number of threads and Timing

One thing that most students will try is to multithread the code. The Makefile provided with the code defines a variable called NUM_THREADS. You should set its value to your number of cores on your machine. Then in your code, you should set the number of threads as omp_set_num_threads(NUM_THREADS) (assuming you are using OpenMP). You could also do something like omp_set_num_threads(NUM_THREADS/2), or omp_set_num_threads(3). When I time your code, I will set NUM_THREADS to the number of physical cores on my machine.

I will time your code by running this script in the root directory of your archive. It may be a good idea to try it just to make sure it runs. (And to let me know ASAP if it is broken.)

What to turn in

You must turn in an archive with all versions of the code, include melange_v0, as well as a project report (README.txt or README.pdf), that explains what you did, why you did it, what worked and what did not, and what performance improvements are achieved in each version. The report doesn’t need to be beautiful prose and can be on the short side, as long as you are precise and explains the above elements.

Your archive should look like this:

% ls
README.pdf  melange_v0  melange_v1
melange_v2  melange_v3  melange_v4
melange_v5  melange_v6  melange_v7
...
Grading

As long as you try a reasonable number of approached, even if many of them do not work, and as long as you have reasonable ideas about whey they might not work, you will get an A on this assignment even if your code doesn’t really go any faster.

Extra Credit

Extra credit will be assigned based on the speedup you achieved and your rank in the class.
