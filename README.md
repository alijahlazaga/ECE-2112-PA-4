# ECE-2112-PA-4

**Made by: Alijah B. Lazaga | 2ECE-B**

The content of this repository contains Experiment  4 for "Data Wrangling and Visualization" this S.Y. 2026-2027.

Note: Before coding, put ⁠`import pandas as pd⁠` and ⁠`import matplotlib.pyplot as plt`⁠ in order to import the PANDAS and MATPLOTLIB libraries and rename them to ⁠pd⁠ and ⁠plt⁠. This way, ⁠pd⁠ and ⁠plt⁠ will act as acronyms, shortening them so that we don't have to code the full library names before every function. We also have to import a .xlsx file that was uploaded in canvas by your professor using `⁠pd.read_xlsx('board2.xlsx')⁠` and name it ⁠df⁠. Since the dataset lacks an ⁠Average⁠ column, we compute it using `⁠df['Average'] = (df['Math'] + df['GEAS'] + df['Electronics'] + df['Communications']) / 4⁠`.

# **A. Visayas Communication DataFrame**

**Create a VisComm DataFrame containing Visayas communication track students with their Name, Gender, Math, Electronics, and Average.**

The following function was used:

• `⁠.loc[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]`⁠ - A built-in function that uses boolean indexing to locate rows where Hometown is Visayas and Track is Communication while selecting specified columns. We then rename the dataframe to ⁠VisComm⁠ using `⁠VisComm = df.loc⁠[]`

**Displaying the total number of rows in VisComm.**

The following function was used:

• ⁠`len(VisComm)⁠` - A built-in Python function that calculates the total row count of the DataFrame.

By combining all of the functions shown above, the final code for this problem is as follows:

```python
import pandas as pd

df = pd.read_csv('board2015.csv')
df['Average'] = (df['Math'] + df['GEAS'] + df['Electronics']) / 3

VisComm = df.loc[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm

len(VisComm)



# **B. Visayas Female DataFrame**

**Create a VisFemale DataFrame containing Visayas female students with their Name, Track, GEAS, Electronics, and Average.**

The following method was used:
• `⁠VisFemale = df.loc[(df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]`⁠ - A python statement that uses boolean indexing to locate rows where Hometown is Visayas and Gender is Female while selecting specified columns.

**Display VisFemale records where the Average score is 60 or higher**

The following method was used:

• `⁠VisFemale[VisFemale['Average'] >= 60]⁠` - A python statement that uses boolean indexing on the ⁠VisFemale⁠ dataframe to filter rows with an Average score greater than or equal to 60 without overwriting ⁠VisFemale⁠.
 
By combining all of the code shown above, the final code for this problem is as follows:

VisFemale = df.loc[(df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale

VisFemale[VisFemale['Average'] >= 60]


# **C. Category-Average Visualization**

**a-b. Calculate mean of the average scores across Track, Gender, and Hometown categories.**

The following function was used:

• `df.groupby('Category')['Average'].mean()`⁠ - A built-in function that groups data by a specific categorical column and computes the mean score for ⁠Average⁠.

**c. Create three bar charts on a consistent y-axis scale comparing group means.**

The following functions were used:

• `⁠plt.subplot(1, 3, slot)`⁠ - A built-in function that creates a 1-row by 3-column plot layout and selects the active grid position (1 = left, 2 = middle, 3 = right).

• `⁠plt.bar(mean.index, mean.values)⁠` - A built-in function that draws vertical bar graphs using category names for x-axis and calculated means for bar heights.

• ⁠`plt.ylim(0, 100)`⁠ - A built-in function that fixes the vertical axis range between 0 and 100 across all subplots for accurate visual comparison.

• `⁠plt.tight_layout()`⁠ - A built-in function that adjusts subplot padding to prevent overlapping titles and axis labels.

By combining all of the code shown above, the final code for this problem is as follows:

import matplotlib.pyplot as plt

track_mean = df.groupby('Track')['Average'].mean()
gender_mean = df.groupby('Gender')['Average'].mean()
hometown_mean = df.groupby('Hometown')['Average'].mean()

track_mean
gender_mean
hometown_mean

plt.subplot(1, 3, 1)
plt.bar(track_mean.index, track_mean.values)
plt.title('Mean Average by Track')
plt.xlabel('Track')
plt.ylabel('Average')
plt.ylim(0, 100)

plt.subplot(1, 3, 2)
plt.bar(gender_mean.index, gender_mean.values)
plt.title('Mean Average by Gender')
plt.xlabel('Gender')
plt.ylabel('Average')
plt.ylim(0, 100)

plt.subplot(1, 3, 3)
plt.bar(hometown_mean.index, hometown_mean.values)
plt.title('Mean Average by Hometown')
plt.xlabel('Hometown')
plt.ylabel('Average')
plt.ylim(0, 100)

plt.tight_layout()

**d. 
Thank you for reading!!!

To fully see the main python program, please visit the link provided below:


### **README file Version History:**

September 16, 2026 - Initial README content uploaded

September 17, 2026 - Final README content uploaded

