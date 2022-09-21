# Homework
# assignment1-YutingZhou866
assignment1-YutingZhou866 created by GitHub Classroom
In this lab we will provide examples how to work with downloadable data in the two most common formats:
* comma-separated-values (CSV) or text files (txt) more generally 
* and Excel or XLS files
We will also provide some basic descriptive analytics, like getting the number of records, defining timeframes or summing up numeric columns.
### Task 1. 
Count the number of neighborhoods and visualize the number of complaints by neighborhood
### Task 2. 
Quantify the average price per square foot per zip code. Visualize result as a bar plot. Which zip codes are the three most expensive ones?
### Task 3.
Visualize only the poorly maintained roads so we can zoom into those that need particular attention.
### Task 4. 
COVID-19 Data by ZIP Code

    a) Aggregate dataset by Borough, calculate total cases amount in each Borough, and then visualize as a barplot
    
    b) Calculate borough-wise positive case percentage among all the tests administered and 
    
    c) among the borough population (%% of populating tested positive), and then visualize as barplots. 

### Data Sources:
https://data.boston.gov/dataset/311-service-requests

https://github.com/CUSP2021PUI/Data/blob/main/RollingSale/'+fname+'?raw=true

https://raw.githubusercontent.com/CUSP2021PUI/Data/main/Street%20Pavement%20Rating.geojson

https://raw.githubusercontent.com/CUSP2021PUI/Data/main/COVID19.csv

### Some Code
1)

boston311['subject'].value_counts().plot.bar()

2)

df=re_sales[['ZIP CODE\n','SALE PRICE\n','LAND SQUARE FEET\n']].groupby(by=['ZIP CODE\n']).sum()

df=df[df['LAND SQUARE FEET\n']!=0]

df=df.apply(lambda x:x[0]/x[1],axis=1)

df.plot.bar()

df.sort_values(axis=0,ascending=False).reset_index().iloc[0:3,:]

3)

rating_poor=rating[rating["rating_word"]=="POOR"]

rating_poor.head()

4)

df[["COVID_CASE_COUNT","TOTAL_COVID_TESTS","BOROUGH_GROUP"]].groupby(by=['BOROUGH_GROUP']).sum().apply(lambda x:x[0]/x[1]*100,axis=1)

df[["COVID_CASE_COUNT","POP_DENOMINATOR","BOROUGH_GROUP"]].groupby(by=['BOROUGH_GROUP']).sum(). \
apply(lambda x:x[0]/x[1]*100,axis=1).plot.bar()
