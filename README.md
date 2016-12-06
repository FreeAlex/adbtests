Test cases for advanced database system


Test 1
-----


T2 should abort, T1 should not, because of kill youngest



Test 2
-----

No aborts happens, since read-only transactions use
multiversion read protocol.

### Output of dump

x1: 101 at site 2
x2: 102 at all sites
All other variables have their initial values.




