Alex Kay writeup

If tables appear "wonky", please click "code" at the top left of the file. Thank you very much and I'm sorry about the inconvenience

For the final project I worked on the “ConcurrentContainers” option. I implemented a working SGL stack and queue, the Treiber stack, M&S queue, an elimination SGL and Treiber stack, and a flat combining SGL stack and queue. I attempted to do (1) and (2) for a total of 300 points. Below are my perf findings and the rest of the writeup. 

EXPERIMENTAL RESULTS AS REQUIRED BY THE PROMPT:
Below are tables for my stacks and queues at 8, 16, and 32 threads. For the sake of comparison I have left the tasks per thread at 10,000 for consistency. Tables are below:
________________________________________________________________________
| Primitive              | Thread Count | Run Time (s) | Throughput    |  
|------------------------|--------------|--------------|---------------|
| SGL stack              |      8       |    0.59      | 10,228,306.64 |                      
| SGL queue              |      8       |    0.55      | 12,517,277.02 |                      
| Treiber stack          |      8       |    0.71      | 831,499.00    |                      
| M&S queue              |      8       |    1.39      | 386,991.81    |                      
| Elim SGL stack         |      8       |    2.00      | 160,303.91    |                     
| Elim Treiber stack     |      8       |    0.92      | 758,574.28    |                      
| Flat SGL stack         |      8       |    2.73      | 134,421.47    |                      
| Flat SGL queue         |      8       |    4.33      | 270,298.79    |                      
|________________________|______________|______________|_______________|
________________________________________________________________________
| Primitive              | Thread Count | Run Time (s) | Throughput    | 
|------------------------|--------------|--------------|---------------|
| SGL stack              |     16       |    1.43      | 532,351.55    |                       
| SGL queue              |     16       |    1.67      | 781,570.11    |                      
| Treiber stack          |     16       |    2.01      | 689,389.11    |                      
| M&S queue              |     16       |    2.80      | 394,357.23    |                      
| Elim SGL stack         |     16       |    4.88      | 158,590.48    |                      
| Elim Treiber stack     |     16       |    2.44      | 633,841.98    |                      
| Flat SGL stack         |     16       |    2.97      | 89,018.31     |                      
| Flat SGL queue         |     16       |    5.35      | 106,327.55    |                      
|________________________|______________|______________|_______________|
________________________________________________________________________
| Primitive              | Thread Count | Run Time (s) | Throughput    |   
|------------------------|--------------|--------------|---------------|
| SGL stack              |     32       |    3.77      | 531,905.21    |                      
| SGL queue              |     32       |    3.85      | 454,236.69    |                      
| Treiber stack          |     32       |    4.11      | 644,987.32    |                      
| M&S queue              |     32       |    5.81      | 397,665.41    |                      
| Elim SGL stack         |     32       |    15.19     | 168,176.74    |                      
| Elim Treiber stack     |     32       |    5.90      | 670,981.67    |                      
| Flat SGL stack         |     32       |    3.48      | 86,545.07     |                      
| Flat SGL queue         |     32       |    5.92      | 69,445.95     |                      
|________________________|______________|______________|_______________|


ANALYSIS OF RESULTS USING PERF AS NECESSARY TO SUPPORT EXPLANATIONS:
Looking at the tables above, we can see that run time grows longer with the more threads we have, which is to be expected. As I attempt to introduce more and more concurrency into my work I end up introducing more contention and waiting as well. This of course isn’t ideal, but it does signify that we are working concurrently, which is the goal of this project. However, as shown via the tables, run time slow down is different depending on what algorithm we look at. 

The SGL stack and queue have a run time that increases consistently as we introduce more and more threads, which is expected. With very few threads there is very little contention, but as the thread count grows threads have to spend more time waiting, hence the constant increase in run time. This is also why the throughput drops a bit as threads increase. Threads are just spending too much time doing nothing.  

The Treiber stack appears to grow pretty consistently as well as the thread count increases to 16 and 32 threads. If we compare the Treiber stack to the SGL stack and queue at 32 threads and look at throughput, we can see that the Treiber stack actually has a better throughput. This is because of the issue with the SGL stack and queue and the way the Treiber stack functions. The Treiber stack doesn’t have waiting threads which causes this algorithm to have a better throughput. But the Treiber stack does have threads that are repeatedly trying a CAS, hence the average performance shown by the Treiber stack. 

The M&S queue grows continuously in run time as we increase threads but the throughput stays about the same despite the thread count, although admittedly pretty low. This is because there is a lot of contention when attempting to enqueue and dequeue. These two areas create constant contention, which prohibits the throughput from changing too much. To summarize, the M&S queue has very stable throughput when we increase thread count, which is something worth noting. That makes the M&S queue great when we’re looking for consistency (remember, run time does increase as threads increase). 

My elimination SGL stack does not run the greatest, I will admit. Increasing thread count doesn't alter the throughput very significantly, but it does cause the run time to spike greatly. When eliminating we are trying to “match” a pop and push together. This clearly doesn’t happen as much as I would like, which causes tons of contention and lots of waiting, two things that we almost always try to admit when creating concurrent algorithms. 

The elimination Treiber stack is very cool to observe. We can see that run time increases rampantly as thread count does the same. But at 32 threads the elimination Treiber stack has the best throughput and only a slightly above average run time. Again, the Treiber stack has threads that are just trying to complete a CAS, meaning threads are always “working”. Although we can have lots of CAS fails we are still guaranteed some form of progress in another thread. These cause the Treiber stack to have the highest throughput at the highest amount of threads, another thing that is definitely worth noting. 

My flat combining SGL stack and flat combining SGL queue follow an expected pattern. Thread count increasing leads to longer run times and lower throughput. Flat combining aims to “serialize” the workload, and with lots of threads this creates a bit of a bottleneck. To visualize it, lots of threads are trying to fit through a small hole, which just doesn’t work. The “main thread” that is meant to be working on all of the waiting tasks has to work through a lot of things, hence the declining run time and throughput. 


A DESCRIPTION OF CODE ORGANIZATION:
I do my best to keep things easy on the graders, I know they are just as busy as everyone else during this time in the semester. I have all my work in “ConcurrentContainers.cpp”, a “Makefile”, and this “WRITEUP.md” file, that’s it. I also attempted the extra credit in a file named "ConVariables.cpp". My containers file starts with my algorithms then it goes into tying them together (helpers, main, etc.). 
All of my algorithms, except for the flat combining stack and queue, are heavily based upon lecture slides. Professor Joe always provides awesome pseudocode that is very easy to follow and understand. I usually put my faith in these slides and things turn out well, and thankfully this time was no different. 


A DESCRIPTION OF EVERY FILE SUBMITTED:
ConcurrentCounters.cpp: My work for this project. It contains all of my stack and queue algorithms and everything that ties them together. For the final project (no extra credit), the work is in this file. 
Makefile: The file that allows me to run this project. The project is runnable with a “make command” thanks to this file. Nothing special here. 
WRITEUP.md: This current file. My writeup, where I talk about my project. 
ConVariables.cpp: I attempted the condition variables w/o spurious wakeups extra credit for 50 points in this file 


COMPILATION INSTRUCTIONS:
“make” builds the project
“./ConcurrentContainers” is used to execute ConcurrentContainers.cpp. This must be used when trying to test something. 


EXECUTION INSTRUCTIONS, PARTICULARLY FOR ANY RESULTS PRESENTED IN THE WRITE-UP:
“./ConcurrentContainers” is the main executable
“--Alg=<data structure name here>” chooses which structure to use
“-t<num threads here>” is used to determine the number of threads
“-n<tasks per thread here>” is used to determine the tasks each thread receives
“-h” is used to display a help menu

Data structure/Alg names to use:
sgl_stack
sgl_queue
treiber_stack
ms_queue
elim_sgl_stack
elim_treiber_stack
flat_stack
flat_queue

Example syntax:
./ConcurrentContainers --Alg=sgl_stack -t 8 -n 10000
./ConcurrentContainers --Alg=flat_stack -t 16 -n 10000
./ConcurrentContainers --Alg=ms_queue -t 32 -n 10000


ANY EXTANT BUGS:
There are currently no remaining bugs in my code. Some data structures take longer than others to complete but they all work. It is important to keep in mind thread count and tasks per thread when selecting parameters, but everything should fall within expectation.
There are no remaining bugs in my work. 





EXTRA CREDIT PORTION (CONDITION VARIABLES W/O SPURIOUS WAKEUPS):

EXPERIMENTAL RESULTS AS REQUIRED BY THE PROMPT:
I believe I did the extra credit. I attempted to create a quick test for it. A thread grabs the lock and is then put to sleep. The main thread then sets a flag that wakes up the thread sleeping. If the thread wakes, we set another flag indicating it has woken up. This means that the worker thread was not woken up until the main thread woke it up (I attempt to wake up the sleeping thread before the main thread does). 


A DESCRIPTION OF CODE ORGANIZATION:
I create the wrapper then shortly after I create my quick test.


COMPILATION INSTRUCTIONS:
I have two makefiles, one for the final project and one for this extra credit portion. The extra credit portion’s makefile is called “ECMakefile”. To compile you’ll need to do:
“make -f ECMakefile”


EXECUTION INSTRUCTIONS, PARTICULARLY FOR ANY RESULTS PRESENTED IN THE WRITE-UP:
After using “make -f ECMakefile”, there is only one option, run. To do so:
“./ConVariables run”
As “ConVariables” is the main executable. If success is shown it works (assuming my test works).
“-h” can be used to display a help screen. 

ANY EXTANT BUGS:
There are no bugs in this code. I tested it and it seems to run just fine so long as the instructions are followed. 


SOURCES:
Professor Joe's lecture sldies, typical online sources, and links provided by Professor Joe for flatcombining and elimination. 
