# Investigation_of_COVID-19
Examining the survival and death rates of infected patients, and creating a predictive model to predict survival of patient (random forest).<br><br>


This single script is used to examine the survival and death rates of individuals who have recovered or are deceased. Also, in this script are different Random Forest models that are used to predict if an infected patient will recover from the infection. Data is taken from three sources:<br><br>
    - Wolfram Data Repository, which contains in-depth data on infected patients:<br>
    https://datarepository.wolframcloud.com/resources/Patient-Medical-Data-for-Novel-Coronavirus-COVID-19)<br><br>
    - John Hopkins University, which the data is broader and only considers quantitative information rather than medical information:<br>
    https://github.com/CSSEGISandData/COVID-19<br>
      (For a more visually interactive look into the data, visit: https://www.arcgis.com/apps/opsdashboard/index.html#/bda7594740fd40299423467b48e9ecf6)<br><br>
    - Euronews, which is similar to the data that John Hopkins University provides:<br>
        https://www.euronews.com/2020/05/25/covid-19-coronavirus-breakdown-of-deaths-and-infections-worldwide<br>
        (Note that even though the URL link above is not updated to the current link, the provided link will redirect to the most updated webpage.)<br><br><br>
    

### To Run This Script:<br>
    - Simply run all the cells in the Jupyter Notebook and all the information will be populated.
        - This script will download all the necessary datasets from Wolfram and John Hopkins but not Euronews.
            - Because Euronews encrypts their data in JavaScript, Python was not able to decode the JavaScript in the HTML file through web parsing. As a result, the statistics were manually added to the script as of 5/26/2020. 
    
    - Any recently updated versions of these packages should work:
        - Pandas, NumPy, Seaborn, Matplotlib, Sklearn, BeautifulSoup(4)
        

### Summary of Analysis: (As of 5/25/2020)<br>
From the data from Wolfram, there was a survival rate of ~70% out of 443 total cases of confirmed COVID-19 infection who have either recovered or are deceased.<br>
From John Hopkins, the survival rate was ~87% out of 2,577,970 cases of deaths or recovered.<br><br>

Since the data from Wolfram contains more in-depth information on infected individuals, this dataset was the main data analyzed and used for predictive modeling. The two variables that were heavily weighted on by the Random Forest models were age and length of infection (days).<br><br>
The average age of deceased patients was 68 years old, and for those who recovered, the average age was 44 years old.<br>
The death rate for patients between the ages of 55-81 was ~56%<br><br>
The average length of time a deceased patient had the infection (from their first symptom experienced) was 15 days. For recovered patients, it was 19 days.<br><br>
        
The highest accuracy predicted (~95.5%) from the Random Forest variants took in all possible variables from the Wolfram dataset (age, sex, symptoms, previous conditions, and length of infection).<br>
    The second highest accuracy predicted a ~94.6% only using the age, sex, length of infection, and whether or not the patient had a previous condition (true or false instead of spreading each previous condition in the highest performance model). In this model, having a previous condition (in general) was weighted similarly to age with weights of ~0.20 and ~0.22, respectively). However, the length of infection had the largest weight of ~0.56.<br><br>
    
In conclusion, it seems that the longer a patient fought the infection, the more likely they were to survive. In addition, their age also contributed to their survival rate.<br><br>
    
### Conditions of Data and Analysis:<br>
Although the dataset from Wolfram contains significantly more observations (rows) than the 443 analyzed, the data for these observations were incomplete. As a result, they were removed from the analysis because many factors are unclear, such as whether the patient was really infected with COVID-19 and not another viral infection like influenza.<br><br>
Suspiciously, in the Wolfram dataset, there were a few patients who "recovered" within a single or couple days after being confirmed/tested. Biologically, that is highly unlikely as detection of the viral genome in the bloodstream would mean that the patient would need more time to eliminate the virus from the body. To be considered "recovered" in those couple of days would mean that the viral "load" is so small in the bloodstream that testing the blood again for the viral genome would have a high chance of the blood extracted to not contain any viral components. (This should result in a true positive where the body has totally eliminated the virus or a false where the blood extract missed/did not extract the virus.) But then detection in the initial blood test would have been quite small in these cases.

### Script Considerations:
The script is prepared to do analysis on the Wolfram dataset based continent. However, since there is only 443 observations being considered, the data for each continent would be too small for meaningful analysis. <br><br>
The script may take 10-30 minutes to run depending on your CPU.<br>
From previous experiences with Wolfram and the webpage containing a lot of errors, a backup folder with the dataset is avaliable in this repository. Simply copy the backup dataset into the "Data" folder and skip the second cell in the Jupyter Notebook.

<br><br><br>
Version 1.0
