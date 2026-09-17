# ECE-2112-PA-4

The content of this repository contains Experiment No. 4 for "Data Wrangling and Visualization" this S.Y. 2026-2027.

Note: Before coding, put ⁠import pandas as pd⁠ and ⁠import matplotlib.pyplot as plt⁠ in order to import the PANDAS and MATPLOTLIB libraries and rename them to ⁠pd⁠ and ⁠plt⁠. This way, ⁠pd⁠ and ⁠plt⁠ will act as acronyms, shortening them so that we don't have to code the full library names before every function. We also have to import a .csv file that was uploaded in canvas by your professor using ⁠pd.read_csv('board2015.csv')⁠ and name it ⁠df⁠. Since the dataset lacks an ⁠Average⁠ column, we compute it using ⁠df['Average'] = (df['Math'] + df['GEAS'] + df['Electronics']) / 3⁠.

A. Visayas Communication DataFrame
a. Create a VisComm DataFrame containing Visayas communication track students with their Name, Gender, Math, Electronics, and Average.

The following function was used:

• ⁠.loc[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]⁠ - A built-in function that uses boolean indexing to locate rows where Hometown is Visayas and Track is Communication while selecting specified columns.
We then rename the dataframe to ⁠VisComm⁠ using ⁠VisComm = df.loc[...]⁠.
b. Display the total number of rows in VisComm.
The following function was used:
• ⁠len(VisComm)⁠ - A built-in Python function that calculates the total row count of the DataFrame.
By combining all of the functions shown above, the final code for this problem is as follows:




B. Visayas Female DataFrame
a. Create a VisFemale DataFrame containing Visayas female students with their Name, Track, GEAS, Electronics, and Average.
The following method was used:
 ⁠VisFemale = df.loc[(df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]⁠ - A python statement that uses boolean indexing to locate rows where Hometown is Visayas and Gender is Female while selecting specified columns.
b. Display VisFemale records where the Average score is 60 or higher.
The following method was used:
 ⁠VisFemale[VisFemale['Average'] >= 60]⁠ - A python statement that uses boolean indexing on the ⁠VisFemale⁠ dataframe to filter rows with an Average score greater than or equal to 60 without overwriting ⁠VisFemale⁠.
By combining all of the code shown above, the final code for this problem is as follows:



C. Category-Average Visualization
a. Calculate average scores across Track, Gender, and Hometown categories.
The following function was used:
 ⁠df.groupby('Category')['Average'].mean()⁠ - A built-in function that groups data by a specific categorical column and computes the mean score for ⁠Average⁠.
b. Create three bar charts on a consistent y-axis scale comparing group means.
The following functions were used:
 ⁠plt.subplot(1, 3, slot)⁠ - A built-in function that creates a 1-row by 3-column plot layout and selects the active grid position (1 = left, 2 = middle, 3 = right).
 ⁠plt.bar(mean.index, mean.values)⁠ - A built-in function that draws vertical bar graphs using category names for x-axis and calculated means for bar heights.
 ⁠plt.ylim(0, 100)⁠ - A built-in function that fixes the vertical axis range between 0 and 100 across all subplots for accurate visual comparison.
 ⁠plt.tight_layout()⁠ - A built-in function that adjusts subplot padding to prevent overlapping titles and axis labels.
By combining all of the code shown above, the final code for this problem is as follows:
