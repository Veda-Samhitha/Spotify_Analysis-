🎵 Spotify Data Analysis with PostgreSQL

This project focuses on analyzing a Spotify dataset using PostgreSQL. The dataset includes key track attributes like energy, liveness, views, likes, and streaming insights. The SQL queries perform data exploration, ranking, and advanced analytics using window functions.

🎯 Problem Statement
With the increasing popularity of music streaming platforms, understanding listener behavior, track performance, and key music attributes is essential. The goal of this project is to analyze a Spotify dataset to uncover trends, identify high-performing tracks, and generate useful insights using SQL queries.

Key questions addressed in this analysis:
- Which tracks and artists have the highest engagement (likes, views, and streams)?
- What are the most common characteristics of hit songs?
- How do energy and liveness impact a song’s popularity?
- Which platform (Spotify vs. YouTube) generates more streams for certain songs?
- What are the top-ranked tracks per artist based on views?

💡 Solution Approach
The project uses PostgreSQL to perform Exploratory Data Analysis (EDA), aggregation, ranking, and window functions to derive meaningful insights from the dataset.

Step 1: Data Preparation
- The dataset is cleaned to remove inconsistencies (e.g., tracks with zero duration).
- Missing values and anomalies are identified.
- A relational PostgreSQL table is created to store the data.

Step 2: Exploratory Data Analysis (EDA)
- Count the number of unique artists, albums, and tracks.
- Identify the longest and shortest songs in the dataset.
- Examine the most common album types.

Step 3: Track & Streaming Insights
- Identify top-streamed tracks (over 1 billion streams).
- Compute total tracks per artist to understand artist engagement.
- Rank the most-viewed tracks per artist using window functions.

Step 4: Advanced SQL Analytics
- Compute cumulative likes ordered by views.
- Find songs where Spotify streams > YouTube streams.
- Calculate the energy-to-liveness ratio for tracks.
- Determine energy variation within albums.


**Query Optimization Technique**

To improve query performance, we carried out the following optimization process:

- **Initial Query Performance Analysis Using `EXPLAIN`**
    - We began by analyzing the performance of a query using the `EXPLAIN` function.
    - The query retrieved tracks based on the `artist` column, and the performance metrics were as follows:
        - Execution time (E.T.): **7 ms**
        - Planning time (P.T.): **0.17 ms**
    - Below is the **screenshot** of the `EXPLAIN` result before optimization:
      ![EXPLAIN Before Index](https://github.com/Veda-Samhitha/Spotify_Analysis-/blob/main/spotify_explain_before_index.png)

- **Index Creation on the `artist` Column**
    - To optimize the query performance, we created an index on the `artist` column. This ensures faster retrieval of rows where the artist is queried.
    - **SQL command** for creating the index:
      ```sql
      CREATE INDEX idx_artist ON spotify_tracks(artist);
      ```

- **Performance Analysis After Index Creation**
    - After creating the index, we ran the same query again and observed significant improvements in performance:
        - Execution time (E.T.): **0.153 ms**
        - Planning time (P.T.): **0.152 ms**
    - Below is the **screenshot** of the `EXPLAIN` result after index creation:
      ![EXPLAIN After Index](https://github.com/Veda-Samhitha/Spotify_Analysis-/blob/main/spotify_explain_after_index.png)

- **Graphical Performance Comparison**
    - A graph illustrating the comparison between the initial query execution time and the optimized query execution time after index creation.
    - **Graph view** shows the significant drop in both execution and planning times:
      ![Performance Graph](https://github.com/Veda-Samhitha/Spotify_Analysis-/blob/main/spotify_graphical%20view%203.png)
      ![Performance Graph](https://github.com/Veda-Samhitha/Spotify_Analysis-/blob/main/spotify_graphical%20view%202.png)
      ![Performance Graph](https://github.com/Veda-Samhitha/Spotify_Analysis-/blob/main/spotify_graphical%20view%201.png)

This optimization shows how indexing can drastically reduce query time, improving the overall performance of our database operations in the Spotify project.
---

 🛠 Key Analyses Performed
 **1️⃣ Exploratory Data Analysis (EDA)**
- Counting unique artists, albums, and channels.
- Identifying the longest and shortest tracks.
- Checking data consistency (e.g., tracks with **zero duration**).

 **2️⃣ Track and Streaming Insights**
- Identifying **the most streamed tracks** (over 1 billion streams).
- Counting **total tracks per artist**.
- Ranking **the most-viewed tracks per artist** using **window functions**.

 **3️⃣ Advanced SQL Analytics**
- **Cumulative sum of likes ordered by views**.
- Identifying tracks where **Spotify streams > YouTube streams**.
- Finding the **energy-to-liveness ratio** for tracks.
- Computing the **difference between the highest and lowest energy values** per album.

Technology Stack
- **Database**: PostgreSQL
- **SQL Queries**: DDL, DML, Aggregations, Joins, Subqueries, Window Functions
- **Tools**: pgAdmin 4 , PostgreSQL 

How to Run 
1. Install PostgreSQL and pgAdmin.
2. Set up the database schema and tables using the provided normalization structure.
3. Insert the data into the respective tables.
4. Execute SQL queries to solve the problems.
5. Explore query optimization techniques for large datasets.


This project is licensed under the MIT License.
