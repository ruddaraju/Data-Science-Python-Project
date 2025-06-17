# OVERVIEW

This is my data analytics project, where I analysed data related job postings and information such as salaries and skills needed for each job. Through this project, I hoped to further improve my data analytics skills and expand my knowledge on certain libraries such as pandas, matplotlib, and seaborn. I also wanted to find insights on which skills were most in demand and highest paying for data related roles. I found this salary and employee data from Luke Barousse's python course, where I was able to establish a strong foudation in data analytics. 

# QUESTIONS
  These are the questions that I intended to answer through data visualization.
  1) What are the most in demand skills for Data Analysts?
  2) How do the skills demanded change over the course of a year?
  3) What are the median salaries for skills that are frequently demanded?
  4)  What are the most optimal skills to learn to get a high paying role in a data role?

# Tools Used
  - Python (libraries)
      - Pandas. Used to clean, filter, and manipulate dataframes in order to create visualizations
      - MatPlotLib. Used to create basic visualizations that can answer some of the questions above and give insights into the job market.
      - Seaborn. Used to create more advanced visualizations that can offer more visually appealling visualizations and offer more layers of information
  - Jupyter notebook
      - Used to write python scripts and compare outputs of dataframes and visualizations
  - VSCode
      - The main IDE I Used to run python scripts
  - Git/GIthub
      - Used to share my project
   
  # Initial Data Cleaning & Filtering
  The Dataset originally contained the column named 'date_posted' (representing the date the job was posted as a string). I converted it into a datetime object for easier manipulation later on. Secondly, the 'job_skills' column contained the skills for each job as a string containing a list ('[python,r,sql]'). I then used the ast library and the literal_eval() function to convert this string into a list. Due to the size of the dataset, for some visualizations I chose to only analyze American roles. I did so by filtering the dataframe by the 'job_country' column. 

```python
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

# Part 1

For the first question. I wanted to find the top 3 most frequent roles in the dataset. This ultimately was for Data Analysts, Data Scientists, and Data Engineers. From here I used the explode() method and aggregated the data to find the counts for each role and for each skill. After sorting the counts, I was able to find the most frequently posted skills for each role. I then was able to convert the counts to percentages of the total job postings for each role, this allows for the counts to be better represented. 

(images/SkillsDemanded.png)

