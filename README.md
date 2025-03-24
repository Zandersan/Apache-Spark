# Apache Spark - Similar Movies Finder

Technology used: Python, AWS (EMR on EC2, S3), Apache Spark, PySpark

## Abstract

The main goal of this project was to analyze 27 million movie ratings for 58,000 movies, provided by 280,000 users.  
Due to the large volume of data, I utilized a cluster of three m5.xlarge instances to process the data.  
I used PuTTY to log into the cluster. The outcome of the project was a list of the 10 most similar movies to  
"Star Wars: Episode IV - A New Hope" (1977), along with their ratings and similarity scores/strengths.  

## Process

1. Created an EMR cluster with three m5.xlarge instances ($0.224/hr per instance) and set up the PuTTY terminal.  
2. Created an S3 bucket with the input data and Python script.  
3. Prepared the movie-similarities-27m.py script using pyspark.sql.  
4. Ran the cluster and submitted the job.  
5. Terminated the cluster (the job was completed in about 15 minutes).  
6. Reviewed the data.  

## Source code

movie-similarities-27m.py:  
https://github.com/Zandersan/Apache-Spark/blob/main/movie-similarities-27m.py  

## Algorithm

The score was calculated using cosine similarity as a measure of similarity between two given movies,  
whose ratings are used as similarity vectors:  

Cosine Similarity Formula:  
https://www.machinelearningplus.com/wp-content/uploads/2018/10/Cosine-Similarity-Formula-1.png  

- Strength of similarity: Represents the number of occurrences of a given pair.  
- Rating: Represents the average rating of a given movie.  

Any movie in the available database could be used for the similarity comparison.  
The selection of the movie occurred by providing its ID as a command-line argument.  

## Output

The outcome was a text file that presented the 10 movies with the highest similarity to  
"Star Wars: Episode IV - A New Hope" according to the algorithm:  

Output file:  
https://github.com/Zandersan/Apache-Spark/blob/main/similar_movies.txt 
