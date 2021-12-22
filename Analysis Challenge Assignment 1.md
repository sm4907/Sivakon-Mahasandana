Author: Mark Mahasandana

A. Criteria 
I was assigned to be a consultant for Alex. She has just returned back from the Army and she would like to pursue a degree in Education. 
She has 4 main criterias, which are as follow: 

1. Safety - She wants to live in the area with low crime rate. For this part, I used data from 2019 Crime in the United States, which listed out more than 8,000 cities based on its population and several types of crimes. From this data, I take five main columns, which are State, City, Population (I will explain this column in the next point), Crimes, which I extract out Violent Crime and Property Crime. The reason I took out only two types of crimes because those two are listed as the main type of crimes. Then, I add the total number of 2 columns together to get one whole number. For this part, I will look for the city that has the least to no crimanal records.

2. Urban - She wants to live in the big city in an urbanized area. Thus, I also extract the population data from the first criteria and use the population data to figure out the college located in the largest city with lowest crime rate. For this part, I will look into the population within the city. I consider cities, which have over 1,000,0000 populations as large cities.

3. Diverstiy - She wants to study in a university with a diverse culture. For this part, I assume based on the school's total student bodies. So that, I use my assumption that schools with higher numbers of students would be classified as having more diverse groups of student bodies. The dataset is given under the "College Scorecard" file. From the "College Scorecard" file, I pick five main columns, which are Institutional Names, City, States, Admission Rates (which I will explain next), and Total numbers of students.  I consider schools with more than 5,000 students as large school.

4. Quality - As mentioned on the third criteria, I used the "Admission Rate" column to measure the quality of the schools. I consider school with less than 10% as very selective schools.

B. Steps
Import - I import data from the given datasets. 

Clean - I cleaned data into two main files. The first data is from "2019 Crime in the United States." As mentioned, I clean up the dataset and eliminate the columns down to four main columns and use filter to find out city with the highest numbers of populations. I, then, label the dataset as Table_2. For the second data, it is from the "College Scorecard". I clean up the dataset and eliminate columns down to five main columns. Then, I label dataset as Table_1.

Prepare - I save two Excel files on my computer's domain account,"User", which is "Sivakon.M" under "This PC" folder.

Merge Data - Since my knowledge in Python is pretty fundamental, I, therefore, utilize the VLOOKUP formula from Microsoft Excel to merge Table_1 and Table_2 data. The College scorecard dataset is listed below.

C. College Scorecard Dataset 


```python
import pandas as pd
Table_1 = pd.read_csv("Table_1.csv")
Table_1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Institution</th>
      <th>City</th>
      <th>State</th>
      <th>Admit Rate</th>
      <th>Total Undergraduate</th>
      <th>Population</th>
      <th>Total Crime (Violent + Property)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Stanford University</td>
      <td>Stanford</td>
      <td>CA</td>
      <td>5.69%</td>
      <td>6,980</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harvard University</td>
      <td>Cambridge</td>
      <td>MA</td>
      <td>5.84%</td>
      <td>7,278</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Yale University</td>
      <td>New Haven</td>
      <td>CT</td>
      <td>7.05%</td>
      <td>5,422</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Princeton University</td>
      <td>Princeton</td>
      <td>NJ</td>
      <td>7.41%</td>
      <td>5,234</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Columbia University in the City of New York</td>
      <td>New York</td>
      <td>NY</td>
      <td>7.42%</td>
      <td>7,970</td>
      <td>8,379,043</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>65</th>
      <td>University of North Carolina at Chapel Hill</td>
      <td>Chapel Hill</td>
      <td>NC</td>
      <td>27.59%</td>
      <td>17,882</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>66</th>
      <td>University of Arkansas at Pine Bluff</td>
      <td>Pine Bluff</td>
      <td>AR</td>
      <td>27.70%</td>
      <td>2,503</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>67</th>
      <td>Reading Hospital School of Health Sciences</td>
      <td>Reading</td>
      <td>PA</td>
      <td>28.10%</td>
      <td>367</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>68</th>
      <td>Babson College</td>
      <td>Wellesley</td>
      <td>MA</td>
      <td>28.21%</td>
      <td>2,106</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>69</th>
      <td>Chicago State University</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>28.65%</td>
      <td>4,321</td>
      <td>2,707,064</td>
      <td>18.0</td>
    </tr>
  </tbody>
</table>
<p>70 rows × 7 columns</p>
</div>



D. Result
Based on my finding, I would recommend Maria to attend Columbia University in the City of New York. The school is located in New York City, which has over 8 million populations. With such a large number of population, New York City would consider as a large city with bigh city life. The city only has 11 reported total crime cases, which is low and classified as low crime rate city. The school has almost 8,000 undergraduate students. Thus, the school has students with very diverse culture. Lastly, the school has 7.42% admitted rate, which is quite low. Therefore, it is clear to say that the school has one of the best educational programs.

Kindly note that the "NaN" stands for No Available Data. There are good amounts of NaN results. However, I was able to find the target school for Alex. 
