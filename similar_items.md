# Similar Items

### Jaccard Similarity
If we have two sets, S and T, the Jaccard similarity is the ratio of the size of their intersection and the size of their union.

### Jaccard Distance
The Jaccard distance is 1 minus the Jaccard Similarity.

Here is an example using two vectors:

1111000000
0100100101

The size of their intersection is 1, since they only share 1 element in the second position.
The size of their union is 7, since they share 7 unique elements in total.

Thus, the Jaccard similarity is 1/7 and the Jaccard distance is 6/7.

Here is an example comparing columns within a matrix:

 | C1 | C2 | C3 | C4
--- | --- | --- | --- | ---
R1 | 0 | 1 | 1 | 0
R2 | 1 | 0 | 1 | 1
R3 | 0 | 1 | 0 | 1
R4 | 0 | 0 | 1 | 0
R5 | 1 | 0 | 1 | 0
R6 | 0 | 1 | 0 | 0

Comparing columns C1 and C2, we find that the size of the intersection is 0, and the size of their union is 5; thus the Jaccard similarity is 0 and the Jaccard distance is 1.

### Euclidian Distance
This is the common definition of "distance" between two points. It will return the linear distance between two points.

If we have two points (2, 7) and (6, 4), the euclidian distance is:

sqrt((2-6)^2+(7-4)^2) = 5


### Cosine Distance
We can compute this by first getting the cosine of the angle between two vectors and then apply the arc-cosine function to translate that result into an angle in the 0 to 180 degree range.

So, to compute the cosine distance, we first take the dot product and divide by the product of the lengths of the two vectors. The dot product is the sum of the products of the corresponding components. The length of a vector is the square root of the sum of the squares of its components.

If we have two vectors of [1, 2, -1] and [2, 1, 1] then the dot product is [1*2+2*1+ -1*1] --> 3

The product of the lenghts of the two vectors is sqrt(1^2 + 2^2 + -1^2) = sqrt(6) * sqrt(6) = 6

So the final result is 3 / 6 = 1 / 2 and the angle whose cosine is 1 / 2 is 60 degrees; the cosine distance between the two vectors.


### Edit Distance
The edit distance is the sum of the lengths of the words minus twice the length of the longest common subsequence. For instance, the longest common subsequence of "his" and "hers" is "hs", so their edit distance is |his| + |hers| - 2|hs| = 3 + 4 -2*2 = 3.

### Shingling
This method constructs a set of short strings from each document to be processed for similarity. For example, if the document contents is the string abcdabd, and we chose k=2 for a set of k-shingles, then the result will be {ab, bc, cd, da,bd}. The result is a set here, so ab only appears once in the result while it appears twice in the original document.

### Minhashing
A MinHash can be used to more efficiently answer the question of similarity. Jaccard similarity does the job, but it is inefficient for larger data sets. Minhasing saves integers instead of strings and compares the integers.
