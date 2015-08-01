# Frequent Itemsets and Association Rules

## Market-Basket Model
We consider items and baskets (or transactions). Each basket consists of a set of items. A set of items that appears in many baskets is considered to be frequent. In a practical situation, we may want to find an association rule that applies to at least 1% of all baskets, and which has a confidence of 50%.

### Support Threshold
A formal measure of the number of of baskets for which a specified set of items is a subset. So, if we define a set to be k, then the support, s, for k is the number of baskets that contains k as a subset. So, k would be considered frequent if if its support is s or more.

## Association Rules
We formalize an association rule as K => j where K is a set of items {K1, K2, K3, ... Kn} and j is an item. If all the items in K appear within a basket, then j is likely to appear as well.

### Confidence of the Rule
The confidence of the rule will tell us how likely the given association rule is to occur, and the confidence is defined as the ratio of the support for K U {j} to the support for K:

Confidence = support for K U {j} / support for K

So, the confidence of the rule is the fraction of the baskets with all of K that also have j. We may only want to search for rules that have above a given confidence, such as higher than it would be if items were placed at random into baskets.

Let this table represent items of B, C, P, M, J within baskets 1 through 8:

table  | B	| C	| P	| M	| J
---------|----|----|----|----|----
1	        | x	 |	   | x  |     |
2       	|	    | x  |	   | x	|
3       	| x	 | x  |			|     | x
4       	|   	|     |	x	 | x  |
5	        | x	 | x  |			| x   |
6	        |     |     |			| x   | x
7	        |   	|     |	x	 |      | x
8	        | x	 | x  |			| x   | x

If we wanted to know the confidence of the rule  J => P, we would calculate it as:

confidence = support for J U {P} / support for J = 1 / 4

### Interest Factor

### Closed Itemsets
A closed itemset is set of items which is as large as it can possibly be without losing any transactions. So to be closed, the itemset must have a larger count than all of its immediate supersets. A triple with a count of 2 cannot be closed unless there are no frequent quadruples or it is contained in none of the frequent quadruples.

### Maximal Itemsets
This is a frequent itemset where none of its immediate supersets are frequent. If the dataset is small, one way to find the maximal itemset is to list all of the frequent itemsets (those at or above the support threshold). To be maximal, one of these sets must not be contained in any other set on this list. So, a maximal frequent itemset is a frequent itemset which is not contained in another frequent itemset. Unlike closed itemsets, maximal itemsets do not imply anything about transactions.

### A-Priori Algorithm
We can use algorithms to help us find the frequent itemsets. The A-Priori algorithm uses two passes over the data.

In the first pass, two tables are created. One table to translate names into integers, if necessary, and another table to keep counts. The algorithm will pass over all the baskets and read each of their contents, translate names into integers and add a count of 1 to each integer (which acts as the index of the item in an array).

In the second pass, we count all the pairs that consist of two frequent items (a pair cannot be frequent unless both of its elements are frequent). At the end of the second pass, we examine the structure of counts to determine which pairs are frequent. 
