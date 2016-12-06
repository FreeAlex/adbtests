Test cases for advanced database system

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













