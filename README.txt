Ans 1 : Ans1.da is the file which separates out original lamport mutex() method into 3 methods. 3 methods are :
	i)   sendRequest()
	ii)  criticalSection()
	iii) releaseRequest()


The problem with this approach is that it can lead to deadlock as we are removing any of the request resource of a process(when a process got the release resource command) from the queue. Rather we should delete that request which has the minimum clock value since that request got the critical section and finished its execution. So the program which is free of deadlock is in file Ans1_withoutdeadlock.da which removes minimum value command from the queue.

Point To Note : On Mac, I am getting authenticationException error when number of processes reached above 10. So I generally tested my code on less than 10 processes. Also for some unknown reasons as well I am getting this authenticationException so its better to run the command again after getting this error.

Ans 2 : answer is in file ans2.pdf

Ans 3 : Code is in file main.da. Here we are comparing correctness and performance for each of the algorithms :

	i)   MyLamport (class MyLamport)
	ii)  OldLamport (class OldLamport)
	iii) SpecLamport (class SpecLamport)

For correctness, we are creating 3 files:

	i)   (Correctness_MyLamport.csv)
	ii)  (Correctness_OldLamport.csv)
	iii) (Correctness_SpecLamport.csv)

each of which contains (Iteration number, No of Processes, No of Requests, Safety, Liveliness) for each of the algorithm.

To check Safety we checked whether 2 processes are at the critical section at the same time. If they are, that means safety is violated. If they are not, that means safety is preserved. Algorithm is explained in the code with the comments.

To check Liveliness, we checked for the deadlock scenario using timeout. If the monitor process is waiting for more than 20 seconds to get a finish message from processes that means system is not progressing and deadlock has occurred.

To measure performance we are creating 2 files:

	i)  Performance_VaryingProcesses.csv (when number of requests are fixed and processes are varying with them)
	ii) Performance_VaryingRequests.csv (when number of processes are fixed and requests are varying with them)

So we used the timeIt module of python to evaluate the execution time. When Processes are varying we run Lamport Algorithms over a fixed number of requests and compute the average times over number of runs. Similarly I did this for number of requests varying case. From my observation, I found out that MyLamport algorithm runs slowly than original and spec lamport algorithms due to interleaving of messages.