# Matrix-Vector Multiplication with MapReduce

This is an example method that is needed in applications such as Google's PageRank. When the matrices and vectors become very large, MapReduce becomes a good option to perform the calculation.

Let's say we have a matrix m and vector v. The columns in the matrix must equal the rows in the vector.

Take the first row of the matrix and perform the dot product with the vector column. In the case of a second matrix, perform the dot product with the first column of that matrix.

### Dot Product
This is an algebraic operation that takes two equal-length sequences of numbers and returns a single number.

### Map Function
The map function will output the following key-value pair:

(i, mij vj)
where i is the row, and j is the column in mij and j is the jth element in vj

Example:

Matrix, m

1	    2	    3	    4
5	    6     7	    8
9	    10	 11	 12
13	14	  15	16

Vector, v

1
2
3
4

The resulting matrix-vector multiplication with MapReduce will produce the following key-value pairs:

(1, 1) (1, 4) (1, 9) (1, 16)
(2, 5) (2, 12) (2, 21) (2, 32)
(3, 9) (3, 20) (3, 33) (3, 48)
(4, 13) (4, 28) (4, 45) (4, 64)

### Reduce Function
The reducer will take all of the key-value pairs from the mappers and sum up the values for each key. This will complete the dot product.

The reduce function will output the following pairs: (i, xi)

This will produce the single column vector that is supposed to be the result of this type of multiplication.

_________________________________________

# Matrix Multiplication with MapReduce in Two Steps
This is similar to matrix-vector multiplication, except that the vector is now a matrix of size i x j. The columns in  matrix M must equal the rows in matrix N. Again, we take the dot product.

## First MapReduce Step

We have j number of columns and i number of rows in M.

We have k number of columns and j number of rows in N.

### Map Function
Each mapper will produce the following key-value pair. The key is the column number of the element. The output of the first map function will have j different keys (the number of columns of M, the first matrix). The output will have i number of value pairs for each key (the number of rows in M, the first matrix). Similarly for the second matrix, N. So, there are only j different keys among all the pairs generated.

(j, (M, i, mij ))
where i is the row, and j is the column in mij

(j, (N, k, njk ))
where j is the row, and k is the column in njk

M and N are the names of the matrices in order to keep track of where each pair originated.

The elements associated with a given key (i,k) are all the elements of the i-th row of M and all the elements of the k-th column of N.

The total number of key-value pairs will be j(i+k).

### Reduce Function
The input to the first Reduce function has one pair for each value j, where j is both a column number of M and a row number of N. Each reducer will produce the following for each key j by multiplying the values  :

((i, k), mij njk)

## Second MapReduce Step
This second step will perform grouping and aggregation with a second MapReduce process.

### Second Map Function
The map function will produce the same key-value pairs: ((i, k), mij njk)

The output of the second Map function has ijk pairs.

### Second Reduce Function
The reduce function will sum up the list of values associated with each key (i, k); the result being:

((i, k), v)

_________________________________________

# Matrix Multiplication with MapReduce in One Step

### Map Function
The mappers will produce the following pairs for each matrix:

((i, k), (M, j, mij)) for k = 1 through n columns in M
where i is the row, and j is the column in mij

((i, k), (N, j, njk)) for k = 1 through n columns in N
where j is the row, and k is the column in njk

### Reduce Function
The reducers will aggregate and sum the values for each key by performing the dot product. There should be one reducer for each cell in the resulting matrix.

key = (i, k)
value = Sumj (mij njk)
