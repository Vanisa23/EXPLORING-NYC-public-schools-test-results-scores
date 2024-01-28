# EXPLORING-NYC-public-schools-test-results-scores
This is an analysis project

In this project I will:

Create a pandas DataFrame called best_math_schools containing the "school_name" and "average_math" score for all schools where the results are at least 80% of the maximum possible score, sorted by "average_math" in descending order.

Identify the top 10 performing schools based on scores across the three SAT sections, storing as a pandas DataFrame called top_10_schools containing the school name and a column named "total_SAT", with results sorted by total_SAT in descending order.

Locate the NYC borough with the largest standard deviation for "total_SAT", storing as a DataFrame called largest_std_dev with "borough" as the index and three columns: "num_schools" for the number of schools in the borough, "average_SAT" for the mean of "total_SAT", and "std_SAT" for the standard deviation of "total_SAT". Round all numeric values to two decimal places.


**Description:**
This project analyzes SAT performance data of various schools, focusing on identifying top-performing schools based on different criteria. It includes filtering schools with the highest average math scores, determining the top 10 schools with the highest total SAT scores, and calculating the borough in New York City with the largest standard deviation in total SAT scores. Additionally, it provides insights into the mean and standard deviation of total SAT scores specifically for Manhattan schools. The analysis combines statistical and data visualization techniques to showcase the educational landscape in terms of SAT performance.

**Technologies Used:**
- Python
- Pandas
- Plotly Express
- Pyppeteer (for PDF export)
- Jupyter Notebook

This project leverages Python's data analysis and visualization libraries, utilizing Pandas for data manipulation and Plotly Express for interactive and visually appealing charts. The Jupyter Notebook environment is employed for coding and analysis, and Pyppeteer is used for PDF export functionality. The project showcases the power of data science tools in extracting meaningful insights from educational datasets.
