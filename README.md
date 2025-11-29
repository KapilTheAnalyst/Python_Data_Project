# The Analysis

## What are the most demanded skills for the top 3 most popular data roles ?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:
[2_Skills_Count.ipynb](3_Project/2_Skills_Count.ipynb)


### Visualize Data

```python
fig,ax = plt.subplots(len(job_titles),1)

for i,job_title in enumerate(job_titles):
    df_plot=df_skills_perc[df_skills_perc
    ['job_title_short']==job_title].head(5)[::-1]
    sns.barplot(data=df_plot,x='skill_percent',y='job_skills',ax=ax[i],hue='skill_count',
    palette='dark:b_r')
plt.show()
```
### Result

![Visualization of Top Skills for Data Nerds](3_Project/images/skill_demand_all_data_roles.png)

### Insights
* Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).
* SQL is the most requested skills for Data Analysts and Data Scientists, with it in over half the job posting for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.
* Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analyst and Data Scientist who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).

## 2. How are in-demand skills trending for Data Analysis ?

### Visualize Data

```python
from matplotlib.ticker import PercentFormatter

df_plot = df_da_us_percent.iloc[: , :5]
sns.lineplot(data=df_plot, dashes=False,legend='full' , palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()
```
### Results
![Trending Top Skills for Data Analysis in the US](3_Project/images/Trending_Top_Skills_In_United_States.png)

*Bar graph visualize the trending top skills for data analysis in the US in 2023.*

### Insights:
- SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
- Excel experienced a significant increase in demand starting around September, surpassing both Python and Tableau by the end of the year.
- Both Python and Tableau show relatively stable demand throughout the year with some fluctuations.

## 3. How well do jobs and skills pay for Data Analysts ?

### Salary Analysis for Data Nerds

### Visualize Data

```python
sns.boxplot(data=df_us_top6, x='salary_year_avg', y='job_title_short', order=job_order)

ticks_x = plt.FuncFormatter(lambda y,pos: f'${int(y/1000)}K')
plt.gca.xaxis.set_major_formatter(ticks_x)
plt.show()
```

#### Results
[Salary Distributions of Data Jobs in the US](3_Project/images/Top_6_Data_Roles_Median_Salary.png)

*Box plot visualizing the salary distributions for top 6 data job titles.*

### Insights
- There is significant variations of salaries across different job titles. Senior Data Scientist positions tend to have the highest salary potential, with up to $600 K, indicating the high experience in the industry.

- Senior Data Engineer and Senior Data Scientist roles show a considerable number of outliers on the higher end of the salary spectrum, suggesting thta exceptional skills or circumstances can lead to high pay in these roles. In contrast, Data Analyst roles demonstrate more consistency in salary, with fewer outliers.

- The median salaries increase with the seniority and specialization of the roles. Senior roles (Senior Data Scientist, Senior Data Engineer) not only have higher median salaries but also larger differences in typical salaries, reflecting greater variance in compensation as responsibilities increase.






