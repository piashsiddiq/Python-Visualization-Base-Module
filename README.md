# Python-Visualization-Base-Module

## 1: LINE CHART / PLOT
#plt.plot(x, y, color='color name', linestyle='line_Style', linewidth=value, marker='marker symbol', label='label name')
#plt.xlabel('text')
#plt.xlim(start, end)

import matplotlib.pyplot as plt

months = [1, 2, 3, 4]
sales = [1000, 1500, 1200, 1800]

plt.plot(months, sales, color='blue', linestyle='--', linewidth=2, marker='o', label='2025 sales data')
plt.xlabel('Months')
plt.ylabel('Sales per month')
plt.title('Monthly Sales Data Report')
plt.legend(loc='upper left', fontsize=12)
plt.grid(color='gray', linestyle=':', linewidth=1)
plt.xlim(1, 4)
plt.ylim(0, 2000)
plt.xticks([1, 2, 3, 4], ['M1', 'M2', 'M3', 'M4'])
plt.show()


## 2: BAR CHART / BAR PLOT

# plt.bar(x, height, color='color name', width=value, label='label name')

import matplotlib.pyplot as plt

product = ['A', 'B', 'C', 'D']
sales = [1000, 1500, 800, 1200]

plt.bar(product, sales, color='orange', label='Sales 2025')
plt.xlabel('Product')
plt.ylabel('Sales')
plt.title('Product Sale Comparison')
plt.legend()
plt.show()



## 3: PIE CHART / PIE PLOT
import matplotlib.pyplot as plt

# Data
regions = ['North', 'South', 'East', 'West']
revenue = [3000, 2000, 1500, 1000]

# Create pie chart
plt.pie(
    revenue,
    labels=regions,
    autopct='%1.1f%%',
    colors=['gold', 'skyblue', 'lightgreen', 'coral']
)

# Add title
plt.title('Revenue Contribution By Region')

# Show plot
plt.show()


## 4: HISTOGRAM
# HISTOGRAM
import matplotlib.pyplot as plt

# List of student scores
scores = [55, 63, 67, 70, 64, 63, 69, 73, 75, 77, 68, 78, 67, 57, 87, 81, 60, 74, 81, 69, 72, 75, 82, 68, 85, 70, 73, 68, 77]

# Plot histogram
plt.hist(scores, bins=7, color='lightgreen', edgecolor='black')

# Add labels and title
plt.xlabel('Score Range')
plt.ylabel('Number of students')
plt.title('Score Distribution of Students')

# Display plot
plt.show()

## 5: Scatterplot
import matplotlib.pyplot as plt

# Sample data
hours_studies = [1, 2, 3, 4, 5, 6, 7, 8]
exam_scores =  [50, 55, 60, 65, 70, 75, 80, 85]

# Scatter plot
plt.scatter(hours_studies, exam_scores, color='green', marker='*', label='Student Data')

# Labels and title
plt.xlabel('Hours studied')
plt.ylabel('Exam Score')
plt.title('Relationship Between Hours Studied and Exam Score')

# Legend and grid
plt.legend()
plt.grid(True)

# Display plot
plt.show()


## 6: DATA CLEANING AND VISUALIZATION

# Step 1 - import the libraries
import pandas as pd
import matplotlib.pyplot as plt

# load the data
df = pd.read_csv('netflix_titles.csv')

# clean data
df = df.dropna(subset=['type','release_year', 'rating', 'country', 'duration'])

#BAR
type_counts = df['type'].value_counts()
plt.figure(figsize=(6,4))
plt.bar(type_counts.index, type_counts.values, color=['skyblue', 'orange'])
plt.title('Number of Movies VS TV Shows on Netflix')
plt.xlabel('Type')
plt.ylabel('Count')
plt.tight_layout()
plt.savefig('movies_vs_tvshows.png')
plt.show()

#PIE
rating_counts = df['rating'].value_counts()
plt.figure(figsize=(8,6))
plt.pie(rating_counts, labels=rating_counts.index, autopct='%1.1f%%', startangle=90)
plt.title('Percentage of Content Ratings')
plt.tight_layout()
plt.savefig('content_Ratings_pie.png')
plt.show()

#HIST
movie_df = df[df['type'] == 'Movie'].copy()
movie_df['duration_int'] = movie_df['duration'].str.replace(' min','').astype(int)

plt.figure(figsize=(8,6))
plt.hist(movie_df['duration_int'], bins=30, color='purple', edgecolor='black')
plt.title('Distribution of Movie Duration')
plt.xlabel('Duration (minutes)')
plt.ylabel('Number of Movies')
plt.tight_layout()
plt.savefig('movie_duration_histd.png')
plt.show()

#Scatterplot
release_counts = df['release_year'].value_counts().sort_index()
plt.figure(figsize=(10, 6))
plt.scatter(release_counts.index, release_counts.values, color='red')
plt.title('Release Year VS Number of Shows')
plt.xlabel('Release Year')
plt.ylabel('Number of Shows')
plt.tight_layout()
plt.savefig('release.png')
plt.show()

#BARH PLOT
country_counts = df['country'].value_counts().head(10)
plt.figure(figsize=(8,6))
plt.barh(country_counts.index, country_counts.values, color='teal')
plt.title('Top 10 Countries by Number of Shows')
plt.xlabel('Number of Shows')
plt.ylabel('Country')
plt.tight_layout()
plt.savefig('top10_countries.png')
plt.show()

content_by_year = df.groupby(['release_year', 'type']).size().unstack().fillna(0)

fig, ax = plt.subplots(1, 2, figsize=(12,5))

# first subplot: Movies
ax[0].plot(content_by_year.index, content_by_year['Movie'], color='blue')
ax[0].set_title('Movies Released Per Year')
ax[0].set_xlabel('Year')
ax[0].set_ylabel('Number of Movies')

# second subplot: TV Shows
ax[1].plot(content_by_year.index, content_by_year['TV Show'], color='orange')
ax[1].set_title('TV Shows Released Per Year')
ax[1].set_xlabel('Year')
ax[1].set_ylabel('Number of Movies')

fig.suptitle('Comparison of Movies and TV Shows Released Over Years')
plt.tight_layout()
plt.savefig('movies_tv_shows_comparison.png')
plt.show()
