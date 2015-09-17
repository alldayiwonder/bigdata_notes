# Natural Join with MapReduce

In a natural join of two relations, each pair of tuples from each relation is compared. A new set of tuples are produced only when the compared tuples agree on all the attributes that are common to the two schemas.

The associated tables must have at least one or more pairs of identically named columns.

The columns must be the same data type.


R |        | S  |    |  
:----------: |:----------: |:-------------:|:----------: 
A |	B        | B |		C
0 |		1      | 0 |	1
1 |		2      | 1 |	2
2 |		3      |  2 |		3

To perform a natural join on the two relations R(A,B) and S(B,C) we must first identify the common attributes; in this case column B is common. So, the B column of both relations will be the key and the value will contain the other component and the name of the relation from which it came.

### Map Function

The key-value pairs produced by the mappers will be:

(b, (R, a))
(b, (S, c))

For the above relations, the key-value pairs produced by the mappers will be:

(1, (R, 0))
(2, (R, 1))
(3, (R, 2))
(0, (S, 1))
(1, (S, 2))
(2, (S, 3))

These key-value pairs will be sorted by key automatically by MapReduce before being sent to the reducers.

(0, (S, 1))
(1, (R, 0))
(1, (S, 2))
(2, (R, 1))
(2, (S, 3))
(3, (R, 2))

The final output from the reduce tasks will be:

(1, (R, 0), (S, 2))
(2, (R, 1), (S, 3))

### Reduce Function

The reduce function will combine all the values together that share the same key.
