# LOCALITY SENSITIVE HASHING

## Description: 
LSH refers to a family of functions (known as LSH families) to hash data points into buckets so that data points near each other are located in the same buckets with high probability, while data points far from each other are likely to be in different buckets. This makes it easier to identify observations with various degrees of similarity.

![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/readme.md-images/Screen%20Shot%202022-03-05%20at%209.33.49%20AM.png)

### Example: Finding similar documents
Let’s try to understand how we can leverage LSH in solving an actual problem. The problem that we’re trying to solve:
### Goal: You have been given a large collections of documents. You want to find “near duplicate” pairs.
In the context of this problem, we can break down the LSH algorithm into 3 broad steps:
1. Shingling
2. Min hashing
3. Locality-sensitive hashing

![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/readme.md-images/Screen%20Shot%202022-03-05%20at%209.39.25%20AM.png)

Now let us understand what we have done here in the project:

## Locality Sensitive Hashing for fast approximate nearest neighbor search

We use our ![patches.csv](https://drive.google.com/file/d/1e-11EFHXPW0y6baIjVA-n82SUnenZYHi/view?usp=sharing) patches.csv dataset and get a target image, calculate distance b/w the new image and all the other images in patches.csv to find similar images. This process is computationally expensive in nature and as a new image embedding have to compare with all the 59K+ image patches in the patches.csv file to find the most similar image(nearest neighbor), which in computational complexity notation is an O(N²) problem and will take exponentially more time to retrieve similar images as the number of images increases.

To solve this problem, we will use **locality sensitive hashing(LSH)** which is an approximate nearest neighbor algorithm which reduces the computational complexity to O(log N). In short, LSH generates a hash value for image embeddings while keeping spatiality of data in mind; in particular; data items that are similar in high-dimension will have a higher chance of receiving the same hash value.

Below are the steps on how LSH converts an embedding in a hash of size K-
1. Generate K random hyperplanes in the embedding dimension
2. Check if particular embedding is above or below the hyperplane and assign 1/0
3. Do step 2 for each K hyperplanes to arrive at the hash value

![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/readme.md-images/Screen%20Shot%202022-03-05%20at%209.44.41%20AM.png)

Let’s now look at how LSH will perform the search. Given a new image patch, we will use LSH to create a hash for the given image and then compare the distance from image patches of the pictures of patches.csv dataset which shares the same hash value. In this way, instead of doing linear search over the whole patches.csv dataset we will only do a similarity search with a subset of images which shares the same hash value with the input image. For our project, we are using lsh_search function for an approximate nearest neighbor search. We have found out similar images to a given patch using lsh_search as well as linear search and found that linear search takes around 3 times the time take by lsh search which is very expensive for large data sets.

Here are some outputs from the project we have implemented on LSH Search:

![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/readme.md-images/Screen%20Shot%202022-03-05%20at%209.47.55%20AM.png)
![image](https://github.com/Zaid9597/Locality-Sensitive-Hashing/blob/main/readme.md-images/Screen%20Shot%202022-03-05%20at%209.48.03%20AM.png)
