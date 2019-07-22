You are asked to (1) implement Lamport's distributed mutex exclusion algorithm exactly as he described it in his CACM 1978 time-clocks paper in (different from the programs given in class), (2) describe at least 2 precise ways that the algorithm does not satisfy the specified safety and liveness requirements, and (3) design and implement methods for testing correctness and comparing performance of implementations of 3 distributed mutual exclusion algorithms written in DistAlgo.

For (1), you may reuse most of some example program in DistAlgo (lamutex/orig.da, under da/examples/), but make sure you follow the overall organization of the 5 rules exactly as described in the paper. Be careful. Don't be creative.

For (2), you may find two ways of violating safety, or liveness, or one of each. You need to describe each way precisely and why it violates safety or liveness. You may write an execution trace, draw a message sequence diagram, etc. Be concise. Be creative too if you like.

For (3), you are asked to test correctness and compare performance of implementations of 3 distributed mutual exclusion algorithms written in DistAlgo (your program from (1), lamutex/orig.da, and lamutex/spec.da, under da/examples/). The goal is to better understand these algorithms.

Your main task will be to design and implement methods for testing correctness and performance. Your implementation is expected to be in DistAlgo/Python.

For correctness, your program needs to be able to do a large number of runs on different parameter values, record information about critical sessions, and check that each run is correct.

For performance, your program needs to be able to do several different runs varying a particular parameter, with multiple repetitions of each run, and measure the running times, including elapsed time and total CPU time, and report statistics about them.

You may implement everything yourself or use implementations by others so long as you understand them well. (Reminder: anything that is not your own creation must be given exact sources and credits; follow the requirements on the course syllabus.)

Your program:

Your program must run under Python 3.6.5 and DistAlgo 1.1.0b12 (can just do "pip install --pre pyDistAlgo" if you have pip installed, or download a file from http://distalgo.cs.stonybrook.edu/download, and follow README).

Your main program must be named
"main.da", and must run with a command like the following, where 
"p" is for number of processes, 
"r" is for total number of requests, 
"n" is for number of runs for correctness testing, and 
"d" and "a" are for number of parameter values and number of repetitions, respectively, for performance testing:

python.exe -m da main.da p r n d a

and do the following two sets of tasks:

(1) for each of the different implementations, test correctness of "n" runs, with each run using randomly generated numbers of processes and requests, up to "p" processes and "r" requests.

(2) for each of the different implementations, compare performance of "d" different runs on "p" processes and up to "r" requests evenly spaced each process, and compare performance "d" different runs on up to "p" processes evenly spaced and "r" requests each process, with "a" repetitions for each run. For example, p = 10, r = 20, d = 5, a = 3 means: compare 5 runs on 10 processes and 4, 8, 12, 16, and 20 requests, respectively, each process, and compare 5 runs on 2, 4, 6, 8, and 10 processes, respectively, and 20 requests each process, where each run should be repeated 3 times.

You have the freedom to decide what information to print about the tests and in what table format. They need to clearly show correctness information and performance comparison. In particular, they must include at least safety violations, if any, and running times averaged over repeated runs, in two tables---one for varying request numbers, and one for varying process numbers.
