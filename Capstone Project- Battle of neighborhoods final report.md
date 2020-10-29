# Coursera Capstone Project
## The Battle of Neighborhoods 
### HEMAJA PATOJU - Part 1 : Introduction and Data Sections


### Coursera Capstone - REPORT CONTENT

#### Introduction Section : 
   Discussion of the business problem and the interested audience in this project.
#### Data Section: 
   Description of the data that will be used to solve the problem and the sources.
#### Methodology section: 
   Discussion and description of exploratory data analysis carried out, any inferential statistical testing performed, and if any machine learnings were used establishing the strategy and purposes.
#### Results section: 
   Discussion of the results.
#### Discussion section: 
   Elaboration and discussion on any observations noted and any recommendations suggested based on the results.
#### Conclusion section: 
   Report Conclusion.

### 1. Introduction: Business Problem
   Since the beginning of 2020, Jakarta and many other cities around the world have been under attack by an invisible army called ‘Novel Corona Virus’, also known as ‘Covid-19’. Every effort has been focusing on solving or minimizing problems, including Data Scientists. Data Scientists assessed the situations in places around the world, such as availability, amount, and geographical distribution (i.e. locations) of health infrastructures, such as virus testing centers and authorized hospitals to treat affected patients. In this article, we would like to present a simple analysis for determining strategic locations for the distribution of masks and medical devices for COVID-19 treatment, based on confirmed cases on May 28, 2020, and the red zone areas for “new normal” condition analysis.

### 2. Data
#### A few Identified factors that influence our decision are:
- Covid-19 cases per district “Riwayat File Covid-19 DKI Jakarta”
- Total population in DKI Jakarta 2020 statistik.jakarta.go.id
- 10 most population in DKI Jakarta 2020 per district statistik.jakarta.go.id
- Hospital for treatment covid-19 megapolitan.kompas.com

###### The following data sources are needed to extract/generate the required information:
- Processed covid-19 positive case data collection on 28 May 2020 At 09.00.
- The distribution of mask sales based on the population in the DKI Jakarta area.
- The distribution of mask sales based on 5 districts with the most densely populated populations.
- New datasets (to be created) from Hospital table that contains city, district, along with their latitudes and longitudes.

#### Make sure that we have created a Foursquare developer account and have our credentials handy.

#### Covid-19 cases per district data is collected from : https://raw.githubusercontent.com/cahyati/Coursera_Capstone/master/Standar%20Kelurahan%20Data%20Corona%20(28%20MEI%202020%20Pukul%2009.00).csv")


#### Total population data in DKI Jakarta 2020 data is collected from : https://raw.githubusercontent.com/cahyati/Coursera_Capstone/master/population2020_DKI_Jakarta.csv")


#### Data of covid hospitals in Jakarta is collected from: https://raw.githubusercontent.com/cahyati/Coursera_Capstone/master/Hospital%20for%20treatment%20covid-19.csv")



#### Data from 10 districts most pupulated in DKI Jakarta, 2020.

![image.png](attachment:image.png)

#### According to the information update from Kompas.com (megapolitan.kompas.com), the following hospitals are the existing reference hospitals for Covid-19 testing in Jakarta area:
- RSPI Sulianti Saroso, Jakarta Utara
- RSUP Persahabatan, Jakarta Timur
- RSPAD Gatot Soebroto, Jakarta Pusat
- RSUP Fatmawati, Jakarta Selatan
- RSU Bhayangkara, Jakarta Timur
- RSAL Mintohardjo, Jakarta Pusat
- RSUD Cengkareng, Jakarta Barat
- RSUD Pasar Minggu, Jakarta Selatan
- RSKD Duren Sawit, Jakarta Timur
- RS Pelni, Jakarta Barat
- RSUD Tarakan, Jakarta Pusat
- RSUD Koja, Jakarta Utara
- RSU Pertamina Jaya, Jakarta Pusat

#### Firstly, dropped all the un-necessary columns and renamed the useful columns from hindi to english. And the data set **df_cases** is ready after data cleasning and preprocessing.

#### df_cases

![image.png](attachment:image.png)


#### df_hospital

![image.png](attachment:image.png)

#### df_most_population

![image.png](attachment:image.png)

### 3. Methodology

#### Using OpenCageGeocode, retrieved an API key to get the latitude and longitude positions from the address and viceversa. 

#### Then, we retrived the latitude and longitude of all Covid-19 testing centers in Jakarta that we have checked from the source

![image.png](attachment:image.png)

### 4. Results

#### The population density in Jakarta.

![image.png](attachment:image.png)

#### The population density in Jakarta, per district

![image.png](attachment:image.png)

#### Based on the graph results shown that areas need the distribution of masks the most is Central Jakarta (Jakarta Pusat) with the most populated areas. 
#### Then 5 districts that mostly need for a distribution of masks are Kali Anyar, Kampung Rawa, Galur, Tanah Tinggi, and Kerendang.

![Screenshot%20%28177%29.png](attachment:Screenshot%20%28177%29.png)

###### We can see from the above map, most of the districts are within the main outer ring roads surrounding the city, and others are situated outside the main ring roads. 
###### To solve in our business challenge, we need to show the extent and the distribution medical devices for treatment of COVID-19 positive case-patients within the city of Jakarta based on the number that we obtained from the government site.

![Screenshot%20%28178%29.png](attachment:Screenshot%20%28178%29.png)

We can see that most of the regions in Jakarta are now in the ‘RED’ zone, with the radius of the circle represent the relative extent of Covid-19 distribution in the City of Jakarta.

![Screenshot%20%28179%29.png](attachment:Screenshot%20%28179%29.png)

![Screenshot%20%28180%29.png](attachment:Screenshot%20%28180%29.png)

#### Finally, We can see from the results of the distribution of COVID-19 cases and the location of hospitals, almost all hospitals require a lot of medical equipment for COVID-19 treatment.

### 5. Discussion
The top 100 venues that are within Tarakan Hospital neighborhood and are within a radius of 500 meters of our candidate Covid-19 testing center using FOURSQUARE API. 

Using the Client ID, Client secret and foursquare api link along with the version and the limit and radius values, an url is created. This url is formatted into json format using the request libraried function.

Using this, the nearby venues of TARAKAN hospital are explored. Those are 28


![image.png](attachment:image.png)

#### Based on the results generated by the FOURSQUARE API, we can locate the business site around Tarakan hospital and identify affected business locations in the red zone.

#### Now, we need to tackle is to gain slightly more insights (profile) of the Tarakan hospital area. 
#### To simplify our analysis, we will just use the Euclidian (distance-based) clustering technique which is part of the unsupervised machine learning technique. 
In particular, we will use K-means clustering. And with the available data by drawing the curve we find out the best k.

![image.png](attachment:image.png)

From the curve the best K is 3

#### Later, we have divided the data into 3 clusters randomly and assigned the cluster numbers using K means Clustering and different colors accordingly.


![Screenshot%20%28181%29.png](attachment:Screenshot%20%28181%29.png)

This map shows us the clustered areas of the TARAKA hospital neighborhood.


#### The result of analysis is the location of the business which is in the Tarakan hospital neighborhood and is within a radius of 500 meters. 
#### Then, we also get the most congested cluster if businesses apply normal conditions in the red zone, potentially increasing cases of contracting the COVID-19 virus within the area.

### 5. Discussion

- The project aims to provide information to local people who must be alerted to go out of the house from the distribution of the COVID-19 case in Jakarta. 
    It also aims to provide information on areas that are most needed for a lot of mask distribution, according to population density in the area.
- Further, it provides information on which hospitals that need the most medical equipments for COVID-19 treatment, possibly even additional medical personnels (doctors and nurses). 
    It also provides information on the business neighborhood which shall implement Covid-19 health protocol with a high discipline when “new normal” comes.

### 6. Conclusion

- This project helps mask sellers to understand potential distribution areas according to population density in Jakarta. 
- It also helps the distribution of medical devices for corona care to hospitals that are estimated to have a large number of patients or even helps analyzing which hospitals need additional medical personnel (doctors and nurses).
- It will also provide awareness to help business owners who run businesses surrounding the adjacent clusters to be better informed, with the density of people within the business neighborhood.


```python

```
