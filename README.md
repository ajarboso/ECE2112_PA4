# ECE2112_PA4

### I. Instructions:

Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a

Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter

notebook in the dedicated submission bin

### Download the BOard Exam 2 and put it in the same folder with PA4.ipynb

![image](https://github.com/user-attachments/assets/9457fd21-6309-4705-b6ca-73c723344eee)

Then Read the data from an Excel file into a DataFrame

![image](https://github.com/user-attachments/assets/c9cd42de-59fa-46fd-b24d-92573aa0809e)



### ECE BOARD EXAM PROBLEM: 
Using data wrangling and data visualization technique with

storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

1. Create the following data frames based on the format provided:

a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

Code for letter A:
 ```
# Filter rows based on different conditions and reset the index, showing specific columns
Instru = boards.loc[(boards['Electronics']>70)
            &(boards['Track']=='Instrumentation') 
            &(boards['Hometown']=='Luzon'), 
            ['Name', 'GEAS', 'Electronics']].reset_index(drop=1)
Instru
```

Output:

![image](https://github.com/user-attachments/assets/9d1cab0f-bf20-4f0c-93e5-e0149f5eb8de)

Code for letter B:
```
# Calculate the average of specific columns
boards['Average'] = boards[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

# Filter rows based on average and other conditions, then show selected columns
Mindy = boards.loc[(boards['Average']>=55)
        &(boards['Gender']=='Female')
        &(boards['Hometown']=='Mindanao'),
        ['Name','Track','Electronics','Average']].reset_index(drop=1)
Mindy
```

Output for B:

![image](https://github.com/user-attachments/assets/102301b6-2dfd-47c6-963a-6e7b7115fc38)

#### The code for A&B  provides several operations on the data
Filter Based on Conditions:

- Select rows where a specific column e.g., Math is below a certain threshold and display selected columns such as Name, Gender, Track, and Math.

Calculate Average:

- A new column called Average is calculated based on the mean of multiple numerical columns such as Math, Electronics, GEAS, and Communication.
Further Filtering:

- After calculating the average, rows are further filtered based on specific conditions e.g., Average score >= 55, and selected columns are displayed.

2. reate a visualization that shows how the different features contributes to average grade. 

Doeschosen track in college, gender, or hometown contributes to a higher average score?

#### We first group the data by Track, Gender, and Hometown to find the average score
```
import matplotlib.pyplot as plt

# Grouping by Track, Gender, and Hometown to get the mean Average score
track_avg = boards.groupby('Track')['Average'].mean()
gender_avg = boards.groupby('Gender')['Average'].mean()
hometown_avg = boards.groupby('Hometown')['Average'].mean()
```
- ```groupby``` is used to separate the data by the chosen categories.
- ```mean() ``` calculates the average score for each group.

#### Bar plot for Average score by Track

```
# Bar plot for Average score by Track
#Set the figure size
plt.figure(figsize=(6,7)) 

#set average to show in bar in blue color
track_avg.plot(kind='bar', color='blue')

#labels the graph
plt.title('Mean Average Score by Track')
plt.ylabel('Mean Average Score')
plt.xlabel('Track')

#shows the table
plt.show()
```

ouput: 

![image](https://github.com/user-attachments/assets/8d7c256e-7f90-4b05-8fb7-aef42c6b37d4)

#### Bar plot for Average score by Gender

```
# Bar plot for Average score by Gender
#Set the figure size
plt.figure(figsize=(6,7))

#set average to show in bar in orange color
gender_avg.plot(kind='bar', color='orange')

#labels the graph
plt.title('Mean Average Score by Gender')
plt.ylabel('Mean Average Score')
plt.xlabel('Gender')

#shows the table
plt.show()

```

Output:

![image](https://github.com/user-attachments/assets/8400876a-2fd5-4462-b00e-1463fbe1d4f0)

#### Bar plot for Average score by Hometown
```
# Bar plot for Average score by Hometown
#Set the figure size
plt.figure(figsize=(6,7))

#set average to show in bar in green color
hometown_avg.plot(kind='bar', color='green')

#labels the graph
plt.title('Mean Average Score by Hometown')
plt.ylabel('Mean Average Score')
plt.xlabel('Hometown')

#shows the table
plt.show()

Output:

![image](https://github.com/user-attachments/assets/91f286c8-fd9f-4103-b324-a1ff72c41970)

#### Codes used in the 3 Bar plots

- ```plt.figure()``` sets the size of the plot.

- ```plot(kind='bar')``` creates a bar chart.

- Title and label to label the graph.

- ```plt.show``` To show the graph

### Revisions

- Revised the visualization part. 

