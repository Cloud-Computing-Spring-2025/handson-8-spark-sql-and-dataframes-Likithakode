# Social Media Sentiment Analysis with Spark

## **Project Overview**
This project leverages Apache Spark to analyze social media data and uncover insights related to user engagement, sentiment trends, and hashtag popularity. By utilizing Spark SQL and DataFrames, we extract key patterns from user interactions.

## **Prerequisites**
Before running the analysis, ensure you have the following installed:

1. **Python 3.x**
   - [Download Python](https://www.python.org/downloads/)
   - Verify installation:
     ```bash
     python3 --version
     ```
2. **Apache Spark & PySpark**
   - Install PySpark via `pip`:
     ```bash
     pip install pyspark
     ```
   - Verify Spark installation:
     ```bash
     spark-submit --version
     ```
3. **Docker (Optional)**
   - If using Docker for Spark, install Docker and Docker Compose:
     - [Docker Install Guide](https://docs.docker.com/get-docker/)
     - [Docker Compose Install Guide](https://docs.docker.com/compose/install/)

## **Project Structure**
```
SocialMediaAnalysis/
├── input/
│   ├── users.csv
│   ├── posts.csv
├── output/
│   ├── top_hashtags.csv
│   ├── engagement_by_age.csv
│   ├── sentiment_vs_engagement.csv
│   ├── top_verified_users.csv
├── scripts/
│   ├── hashtag_analysis.py
│   ├── engagement_by_age.py
│   ├── sentiment_analysis.py
│   ├── verified_users.py
├── docker-compose.yml
└── README.md
```

## **Dataset**
### 1. `users.csv`
Contains user details including demographics and verification status.

| UserID | Username    | AgeGroup | Country | Verified |
|--------|------------|----------|---------|----------|
| 1      | @john_doe  | Adult    | USA     | True     |
| 2      | @jane_smith| Teen     | UK      | False    |
| 3      | @tech_guru | Senior   | Canada  | True     |

### 2. `posts.csv`
Includes user-generated posts along with engagement metrics and sentiment scores.

| PostID | UserID | Content                     | Timestamp           | Likes | Retweets | Hashtags       | SentimentScore |
|--------|--------|----------------------------|---------------------|-------|----------|---------------|---------------|
| 101    | 1      | Love the new tech update!  | 2023-10-01 14:00:00 | 120   | 50       | #tech,#AI     | 0.9           |
| 102    | 2      | This app keeps crashing.  | 2023-10-02 15:30:00 | 30    | 10       | #bugs         | -0.5          |
| 103    | 3      | Excited for the weekend!  | 2023-10-03 12:00:00 | 70    | 20       | #weekend      | 0.4           |

---

## **Running the Analysis**
You can execute the scripts locally or via Docker.

### **1. Running Locally**
Navigate to the project directory and run each script using `spark-submit`:
```bash
cd SocialMediaAnalysis/
spark-submit scripts/hashtag_analysis.py
spark-submit scripts/engagement_by_age.py
spark-submit scripts/sentiment_analysis.py
spark-submit scripts/verified_users.py
```



## **Analysis Tasks**
### **1. Hashtag Popularity**
**Objective:** Identify the most frequently used hashtags.

- Extract hashtags from `posts.csv`.
- Count occurrences and rank the top 10.

**Expected Output:**
| Hashtag   | Count |
|-----------|-------|
| #tech     | 150   |
| #AI       | 120   |
| #weekend  | 95    |

---
### **2. Engagement by Age Group**
**Objective:** Analyze user engagement based on age group.

- Join `users.csv` with `posts.csv` on `UserID`.
- Compute average likes and retweets for each age group.

**Expected Output:**
| Age Group | Avg Likes | Avg Retweets |
|-----------|----------|--------------|
| Adult     | 80.2     | 30.5         |
| Teen      | 45.1     | 15.8         |
| Senior    | 25.7     | 8.2          |

---
### **3. Sentiment & Engagement**
**Objective:** Determine how sentiment influences engagement.

- Categorize posts as Positive (`>0.3`), Neutral (`-0.3 to 0.3`), or Negative (`<-0.3`).
- Compute average likes and retweets per sentiment category.

**Expected Output:**
| Sentiment | Avg Likes | Avg Retweets |
|-----------|----------|--------------|
| Positive  | 90.5     | 40.3         |
| Neutral   | 50.2     | 20.1         |
| Negative  | 25.8     | 10.5         |

---
### **4. Top Verified Users**
**Objective:** Identify top influencers among verified users.

- Filter users where `Verified = True`.
- Compute total reach (likes + retweets) and rank the top 5 users.

**Expected Output:**
| Username     | Total Reach |
|-------------|------------|
| @tech_guru  | 1700       |
| @john_doe   | 1500       |

---
## **Submission Checklist**
- [✅] PySpark scripts (`scripts/` folder)
- [✅] Output files (`output/` folder)
- [✅] Input datasets (`input/` folder)
- [✅] README.md
- [✅] GitHub repository submission



