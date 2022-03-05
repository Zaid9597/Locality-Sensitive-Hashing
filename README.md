# LOCALITY SENSITIVE HASHING

## Description: 
LSH refers to a family of functions (known as LSH families) to hash data points into buckets so that data points near each other are located in the same buckets with high probability, while data points far from each other are likely to be in different buckets. This makes it easier to identify observations with various degrees of similarity.

## Example: Finding similar documents
Let’s try to understand how we can leverage LSH in solving an actual problem. The problem that we’re trying to solve:
## Goal: You have been given a large collections of documents. You want to find “near duplicate” pairs.
In the context of this problem, we can break down the LSH algorithm into 3 broad steps:
1. Shingling
2. Min hashing
3. Locality-sensitive hashing

![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/Screen%20Shot%202022-03-05%20at%209.33.49%20AM.png)
