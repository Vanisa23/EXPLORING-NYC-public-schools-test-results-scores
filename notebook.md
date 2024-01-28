![New York City schoolbus](schoolbus.jpg)

Photo by [Jannis Lucas](https://unsplash.com/@jannis_lucas) on [Unsplash](https://unsplash.com).
<br>

Every year, American high school students take SATs, which are standardized tests intended to measure literacy, numeracy, and writing skills. There are three sections - reading, math, and writing, each with a maximum score of 800 points. These tests are extremely important for students and colleges, as they play a pivotal role in the admissions process.

Analyzing the performance of schools is important for a variety of stakeholders, including policy and education professionals, researchers, government, and even parents considering which school their children should attend. 

You have been provided with a dataset called `schools.csv`, which is previewed below.

You have been tasked with answering three key questions about New York City (NYC) public school SAT performance.


```python
# Re-run this cell 
import pandas as pd
!pip install plotly
import plotly.express as px

#for html export
import plotly.io as pio
pio.renderers.default = "notebook"

#two lines for pdf export
!pip install Pyppeteer
!pyppeteer-install

# Read in the data
schools = pd.read_csv("schools.csv")

# Preview the data
schools.head()

# Start coding here...
#solution 1
best_math_schools = schools[schools['average_math'] >= 640]
best_math_schools = best_math_schools[['school_name', 'average_math']].sort_values(by='average_math', ascending=False)
print(best_math_schools)


#solution 2
schools["total_SAT"] = schools["average_math"] + schools["average_reading"] + schools["average_writing"]
top_10_schools = schools[['school_name', 'total_SAT']].sort_values(by='total_SAT', ascending=False).head(10)
print(top_10_schools)


#solution 3
stdev = schools.groupby("borough")["total_SAT"].std()
largest_std = stdev.idxmax()
print(largest_std)
num_schools = len(schools[schools["borough"]== "Manhattan"])
manhattan_data = schools[schools['borough'] == 'Manhattan']
# Calculate the mean and standard deviation for total SAT scores in Manhattan
average_SAT = manhattan_data['total_SAT'].mean().round(2)
std_SAT = manhattan_data['total_SAT'].std()
print( str(num_schools), str(average_SAT), str(std_SAT)  )
data = { "num_schools": [num_schools],"average_SAT":[average_SAT],"std_SAT":[std_SAT]}
largest_std_dev = pd.DataFrame(data, index = ["Manhattan"])
print(largest_std_dev) 

# Add as many cells as you like...


```

    Requirement already satisfied: plotly in //anaconda3/lib/python3.11/site-packages (5.18.0)
    Requirement already satisfied: tenacity>=6.2.0 in //anaconda3/lib/python3.11/site-packages (from plotly) (8.2.3)
    Requirement already satisfied: packaging in //anaconda3/lib/python3.11/site-packages (from plotly) (23.1)
    Requirement already satisfied: Pyppeteer in //anaconda3/lib/python3.11/site-packages (1.0.2)
    Requirement already satisfied: appdirs<2.0.0,>=1.4.3 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (1.4.4)
    Requirement already satisfied: certifi>=2021 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (2023.11.17)
    Requirement already satisfied: importlib-metadata>=1.4 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (6.0.0)
    Requirement already satisfied: pyee<9.0.0,>=8.1.0 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (8.2.2)
    Requirement already satisfied: tqdm<5.0.0,>=4.42.1 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (4.65.0)
    Requirement already satisfied: urllib3<2.0.0,>=1.25.8 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (1.26.18)
    Requirement already satisfied: websockets<11.0,>=10.0 in //anaconda3/lib/python3.11/site-packages (from Pyppeteer) (10.4)
    Requirement already satisfied: zipp>=0.5 in //anaconda3/lib/python3.11/site-packages (from importlib-metadata>=1.4->Pyppeteer) (3.11.0)
    chromium is already installed.
                                               school_name  average_math
    88                              Stuyvesant High School           754
    170                       Bronx High School of Science           714
    93                 Staten Island Technical High School           711
    365  Queens High School for the Sciences at York Co...           701
    68   High School for Mathematics, Science, and Engi...           683
    280                     Brooklyn Technical High School           682
    333                        Townsend Harris High School           680
    174  High School of American Studies at Lehman College           669
    0    New Explorations into Science, Technology and ...           657
    45                       Eleanor Roosevelt High School           641
                                               school_name  total_SAT
    88                              Stuyvesant High School       2144
    170                       Bronx High School of Science       2041
    93                 Staten Island Technical High School       2041
    174  High School of American Studies at Lehman College       2013
    333                        Townsend Harris High School       1981
    365  Queens High School for the Sciences at York Co...       1947
    5                       Bard High School Early College       1914
    280                     Brooklyn Technical High School       1896
    45                       Eleanor Roosevelt High School       1889
    68   High School for Mathematics, Science, and Engi...       1889
    Manhattan
    89 1340.13 230.2941395363782
               num_schools  average_SAT    std_SAT
    Manhattan           89      1340.13  230.29414



```python

```
