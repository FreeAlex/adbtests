# Test cases for ADB

**The first 16 test cases (1-16) come from the [webpage](http://cs.nyu.edu/courses/fall16/CSCI-GA.2434-001/projectsampletests.deadlockdetection) owned by [Professor Dennis Shasha](http://cs.nyu.edu/cs/faculty/shasha/), therefore, copyright owned by Denis Shasha. Please contact him if someone want to copy those test cases.**

However, we encourage anyone to contribute.

Please help others as well as yourself.

Test 1
-----
T2 should abort, T1 should not, because of kill youngest

Test 2
-----
No aborts happens, since read-only transactions use
multiversion read protocol.

### Output of dump
```
x1: 101 at site 2
x2: 102 at all sites
All other variables have their initial values.
```

Test 3
-----
T1 should not abort because its site did not fail.

In fact all transactions commit

Test 4
-----
Now T1 aborts, since site 2 died after T1 accessed it. T2 ok.
Normally, we wait till the end(T1) to abort T1.
However, it is ok to abort T1 right away when fail(2) happens. 
Both are correct.

Test 5
-----
T1 fails again here because it wrote to a site that failed. T2 ok.

Test 6
-----
T1 ok. T2 ok. T2 reads from a recovering site, but odd variables only at that site

Test 7
-----
T2 should read the initial version of x3 based on multiversion read consistency.

Test 8
-----
T2 still reads the initial value of x3

T3 still reads the value of x3 written by T1

Test 9
-----
T1, T2, T3 ok. T3 waits and then comlete after T2 commits 

Test 10
-----
T3 should wait and should not abort

Test 11
-----
All should commit

Test 12
-----
both commit

Test 13
-----
T1 and T2 wait

Test 14
-----
They all commits


Test 15
-----
T1 will abort because x4 is on site 2 and  so site 2 will lose its locks in the fail event.
So T1 will abort. T2 will be fine as will the others.


Test 16
-----
T3 must wait till the commit of T2 before it reads x4 
(because of locking), so sees 44.
T1 reads x2=22 at site1

Test 17
-----
All should commit
The final value of x1 can be any one.

Test 20
-----
T4 should not read 101 from invisible servers














