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
