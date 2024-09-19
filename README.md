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




