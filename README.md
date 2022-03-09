# Rockbuster Stealth Data Analysis Project

![This is an image](RackMultipart20220309-4-uuykpi_html_89605f79fb0a2033.png)

**Overview and Purpose**

Rockbuster Stealth LLC is a movie rental company that used to have stores around the world. Facing stiff competition from streaming services such as Netflix and Amazon Prime, the Rockbuster Stealth management team is planning to use its existing movie licenses to launch an online video rental service in order to stay competitive.

**Context**

Rockbuster&#39;s dataset was ready for a relational database management system. In order to answer the questions posed by different departments, they needed someone to query the data using SQL.

See the data dictionary [here](https://coach-courses-us.s3.amazonaws.com/exercises/1054/44753/d6a29bbb69df0b3a897faec29dcf000d/Data_Imm_3.10_DataDictionary_CBoyd.pdf).

Download a .tar of Rockbuster&#39;s database [here](http://www.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip).

**Objective**

The Rockbuster Stealth Management Board has asked a series of business questions and they expect data-driven answers that they can use for their 2020 company strategy.

Here are the main questions they&#39;d like to answer:

- Which movies contributed the most/least to revenue gain?
- What was the average rental duration for all videos?
- Which countries and cities are Rockbuster customers based in?
- Who are the top five customers, by total amount paid, within those countries and cities?
- Where are customers with a high lifetime value based?
- Do sales figures vary between geographic regions?

**Tools and Skills**

![](RackMultipart20220309-4-uuykpi_html_6a41bf0c11992ac3.png) **PostgreSQL:**   Database-Querying Using Basic Rules and Best Practices

• Develop a query plan for scripts to ensure more optimized queries using EXPLAIN for costs

• Use ETL (Extract, Transform, Load) to migrate data from one database to another.

• Cleaning the data—duplicates, non-uniform data, incorrect data, and missing data

• CREATE commands for tables and indexes using CREATE TABLE, INSERT, DEFAULT, and ALTER

• SELECT commands using FROM, WHERE, ORDER BY, LIMIT, GROUP BY, DISTINCT,

• UPDATE commands to modify data using SET and WHERE

• DELETE commands using DROP and WHERE

• Constraint commands using UNIQUE, NOT NULL, PRIMARY KEY, FOREIGN KEY and CHECK

• Aggregate functions with GROUP BY, such as COUNT, SUM, MAX, MIN, AVG

• Filtering with WHERE (BETWEEN [AND, NOT OR, LIKE], OR, IN), GROUP BY, ORDER BY, HAVING, CASE [WHEN, THEN, END])

• Five types of joins: INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN, and multiple joins.

• Create a query within a query using subqueries with inner and outer statements

• Using CTE (Common Table Expressions) in lieu of subqueries

• Exporting query results to .csv files for Microsoft Excel and Tableau

![](RackMultipart20220309-4-uuykpi_html_4efd8586ba25dc5a.png) **Tableau:**  Visualization of Results Following Visual Design Standards

• Spatial analysis using point maps, heat maps, choropleth maps, graduated symbol maps, and combination maps

• Textual analysis using word clouds and packed bubble charts

• Scatterplots and bubble charts

• Statistical visualizations such as histograms and boxplots

• Composition and comparison charts such as treemaps and pie charts

• Frequencies and distributions

• Temporal charts such as line charts, bar and column charts, area charts

- Forecasting using linear extrapolation, averaging, and exponential smoothing

• Create dashboards and a storyboard for presentation purposes.

**Project Steps**

First, I uploaded the dataset to PostgreSQL and then generated an entity relationship diagram (ERD), which is shown below. I chose PostgreSQL as my tool of choice because we were using Rockbuster&#39;s database, and their questions lent themselves to SQL querying. The questions dealt with subsets of the data, and SQL makes it easy to pull specific portions from datasets. The ERD is necessary for the analysis because it shows how the data tables are connected to one another. We needed an understanding of those relationships to combine the tables while querying the data. There were no difficulties with this stage of the project, as the data was ready to be uploaded into a relational database management system, and PostgreSQL has a built-in ERD generator.

![](RackMultipart20220309-4-uuykpi_html_178ba46cfd2b9ac5.png)

Next, I queried the data to answer business questions. These were the most involved steps of the project, requiring SQL expertise. The goal was to come up with result tables that could be exported for visualization.

The select queries required aggregate functions, multiple joins as well as group by, order by, having, and limit clauses. I also used CTE (common table expressions) and subqueries. Fortunately, I was able to save time by taking advantage of the way many of the questions built on one another. I then was able to copiy previous queries and tweak them to create the common table expressions.

A challenge I faced is that more than nine cities—in the top ten countries by customer count—were tied for second in terms of customer count, and Rockbuster wanted the top ten. Moreover, they were tied at a value of one, so any active city was truly in second place. SQL generated ten results, seemingly arbitrarily. In fact, cities 2-9 changed when using a subquery instead of common table expression. To navigate the &quot;multiple-second-place-cities&quot; dilemma, I included a histogram of customer counts in my final analysis after displaying on a point map the top 10 that SQL generated.

![](RackMultipart20220309-4-uuykpi_html_a9603929d7ef75e2.png)

In hindsight, it would have been better to include all the active cities in the table and the point map. This would have drawn more attention to the &quot;many-way&quot; tie. Additionally had this been a true analysis and not for educational purposes, I would have contacted the data engineer, my direct report, and/or client to see if the data they sent us was incomplete/corrupted. After each successful query, I exported the resulting data to .csv for version control and to be easily read by Microsoft Excel and Tableau.

To see the queries individually, see the SQL query project folder [here](https://github.com/nlogan-data/Rockbuster-SQL-Project/tree/main/SQL-Queries).

In Tableau, I made a story board to present my findings to Rockbuster stakeholders. I started with an executive summary, then answer the questions the company posed, and finally displayed some of my own analyses that were discovered. I chose this order to first set the stage and share key results, then show what Rockbuster requested, and finally elucidate with more visualizations of findings.

Although many different charts and graphs were created, only a select few made it to the final presentation. My favorite of the visualizations were the point maps, which were great for geospatial trend spotting. I used size and color to denote the magnitude of the values.

![](RackMultipart20220309-4-uuykpi_html_e742a352b3496286.png)

Other additions to the analysis were a scatterplot, which showed the correlation between a country&#39;s customer count and revenue, and a histogram of the customer count by city. A correlation between customers and revenue is often assumed, but we were able to confirm that assumption with the scatterplot; its trendline had a correlation coefficient very close to 1—a near-perfect correlation. The histogram illustrated the lack of customer depth in active cities, as almost every city had just one customer.

There were no setbacks during the storyboard process, as the visualizations were straightforward.

**Conclusion**

I was able to answer all the questions that Rockbuster asked. The most surprising finding was how many cities had just one customer. If this were not an educational project, I would have reached out to a direct report, data engineer, and/or the client before delivering the final product, to find out whether the lack of customers per city is an error, or not. I did speak with my course mentor about this, mentioning that it may have been a measure to reduce the total amount of data in the dataset. He confirmed this suspicion.

If I were to change anything, I would have included all the active cities in my point map of the top cities by customer count within the top ten countries and explore more questions that came to my mind during this project, that I believed would help Rockbuster enter the online streaming service market and remain competitive.

View my final PowerPoint presentation [here](https://coach-courses-us.s3.amazonaws.com/exercises/1054/44753/2ce7ad8426ccf76531020d2587128f01/Data_Imm_3.10_PPT_Cboyd_PDF.pdf)
