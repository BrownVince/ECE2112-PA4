<div align="center">

# Hi! <img src="https://github.com/user-attachments/assets/d21e6cd6-76a9-4934-8910-809aa4815251" alt="Wave" width="30"/>, I'm Vince Joriz E. Supsup  
From 2ECE-D, and this is my Programming Assignment #4 in ECE2112  
Submitted: Sept. 19, 2024 

</div>

# Version History
V1.0 (09-19-24) - Initial Release  
V2.0 (09-19-24) - Submission of Github link

# Software(s) Used
<img src="https://github.com/user-attachments/assets/32ea11b3-b4e5-4efa-a673-ce2b102ab4b5" alt="Jupyter Logo" width="80"/> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="Github" width="100"/>

# ECE BOARD EXAM PROBLEM:
In this assignment, we are tasked to use data wrangling and data visualization technique with
storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

* The first step that we need to do is to download the board2.xlsx file
* Second step is to create a new notebook then import the pandas library
```
import pandas as pd #Import panda library as pd for easy calling
```
* Then read the downloaded file and save it to a variable
```
bd = pd.read_excel('board2.xlsx') #import the excel file and store it to bd
```
### For Part 1A. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
We are tasked to find who scored 70+ in electronics and who has an instrumentation track that lives in Luzon
```
Instru = bd.loc[(bd['Electronics']>70)
    &(bd['Track']=='Instrumentation')
    &(bd['Hometown']=='Luzon'), ['Name', 'GEAS', 'Electronics']]
Instru

#If a given row/student satisfies all 3 conditions, it will output the columns 'Name', 'GEAS', and 'Electronics' of that row
```
### For Part 1B. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female
* In this problem, the total average score of a student is needed. Hence, we will create a new column named 'Average' containing the average score of a student
```
bd['Average'] = bd[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #We need to set the axis to 1 since the values in the rows are what we would like to add
```
* In this code, we need to find who scored an average of 55+ who lives in Mindanao and is a female
```
Mindy = bd.loc[(bd[('Average')]>=55)
    &(bd['Hometown']=='Mindanao')
    &(bd['Gender']=='Female'), ['Name', 'Track', 'Electronics', 'Average']]

#If a student satisfies all the given conditions, it will print the columns 'Name', 'Track', 'Electronics', and 'Average' of that student
```
### For Part 2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?
* Import matplot library first
```
import matplotlib.pyplot as plt #Importing the matplot library as plt for easy calling
```
* Setting the figure size
```
plt.figure(figsize=(7,7)) #Setting the size of the figure
```
* Creating the bar graph of the relationship between track chosen and average scores
```
track = plt.bar(bd['Track'], bd['Average'])

#Adding names to each component
plt.xlabel('Track')
plt.ylabel('Average')
plt.title('Average Scores by Track')
#The given graph shows that students who took microelectronics averaged a lot higher compared to the others
```
**OUTCOME:**
![Screenshot 2024-09-19 224722](https://github.com/user-attachments/assets/fc6cafea-911b-4ce3-9da2-26fad67a07c1)

* Creating the bar graph of the relationship between gender and average scores
```
track = plt.bar(bd['Gender'], bd['Average'])

#Adding names to each component
plt.xlabel('Gender')
plt.ylabel('Average')
plt.title('Average Scores by Gender')
#This graph shows that females scored a lot higher compared to males
```
**OUTCOME:**
![Screenshot 2024-09-19 224908](https://github.com/user-attachments/assets/793fc447-da18-49d1-a79c-4adea9493d95)

* Creating the bar graph of the relationship between hometown and average scores
```
track = plt.bar(bd['Hometown'], bd['Average'])

#Adding names to each component
plt.xlabel('Hometown')
plt.ylabel('Average')
plt.title('Average Scores by Hometown')
#Students who lives in Luzon averaged a lot higher compared to those who live in Mindanao and Visayas
```
**OUTCOME:**
![Screenshot 2024-09-19 225057](https://github.com/user-attachments/assets/708187ed-7901-4b17-9920-39306f2b9ff2)

