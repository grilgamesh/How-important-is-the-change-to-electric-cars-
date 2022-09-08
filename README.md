# How important is the change to electric cars?
View a slideshow presentation of this readme at https://docs.google.com/presentation/d/1w5KIalZp_sjbLWW5vmZ8nmFyrG-AVmn5aj4jmcooTOQ/edit?usp=sharing

## Technologies implemented:
* Python
* Pandas
* Numpy
* Matplotlib
* Scipy.Stats

## Files in this folder




## Exploration and Data Cleaning
We found our data on “https://carfueldata.vehicle-certification-agency.gov.uk/ “, a reputable government source for data on vehicle testing. The data set comprises 44 columns, detailing text and numerical information on over 6000 cars registered since 2019. Information was given about the cars’ fuel type, engine type, and many statistics about engine power, various kinds of emissions, and so on. Some of this data would be different for different kinds of car, for instance internal combustion engines would not need information on electric power and vice versa.

An important part of the data for our investigation was the WLTP CO2 column, and it’s partner, WLTP CO2 Weighted. We found that there was no consistent use of these two columns; the first applied to petrol and diesel, and the second applied to hybrid cars; however, some hybrid cars also had a value in the first column, and so on. This was compounded by some questionable entries in the weighted column. The weighted column seems designed for those hybrid vehicles that don’t exclusively use fossil fuels, and therefore need the CO2 rating for their internal combustion engine degraded by some amount to reflect their less-than-100% reliance on it. 

We decided that the weighted column was the column to choose, as long as it had a non-zero value in it; in other circumstances, the non-weighted value should be chosen. Therefore code was written to interpret null or 0 values as something to ignore, and in these cases choose the WLTP CO2 column. Thus these two columns were combined into a more robust ‘cleaned co2’ column.

Another instance was presented with the THC + NOx column, which was not consistently filled in. THC represents ‘total hydrocarbons’, and refers to unburnt fuel emissions. NOx is Nitrogen Oxide and Nitrogen Dioxide,substances that emerge in smaller quantities than CO2 but can be many times more damaging. However in the cases of blanks in this column, it was possible to calculate the value from other columns, and this was automated.

In the data there were many duplicate rows with no or few differences and this was puzzling. Should these duplicate rows be reduced to one row each? It was decided to include all of the duplicate rows, since it seemed to reflect production scale of different models - and this could positively impact our analysis by correctly weighting it towards popularity of different vehicles. EG, Rolls Royce have fewer rows for each of their vehicles than Honda, and correspondingly sell fewer cars.

Even after all this consideration, there are still questionable values in the data. These have been left in as it is impossible to remove them all, and there is still the possibility that they are strange but correct. For instance, the Citroen Space Tourer had two specific versions with unusually low weighted CO2 emissions; these did not fit the trend but they have been allowed to remain, but noted as anomalies.


## Popular fuel types
We decided to start our analysis by studying the different types of fuel that are on the market, and which of them consumers are using the most. We plotted some pie charts that show the popularity of fuel type from 2019-2022. As our charts show, the most popular is Petrol giving us an average of 49.7% of popularity through the years and the second most popular is diesel with 24.3%. We also noticed a slight shift of fuel type usage in the year 2020 compared to the year 2019. It is noticeable that consumers started switching to more hybrid fuel types, although the change is slight as petrol and diesel are still the most popular in these years. In the year 2021 hybrid fuel type, petrol electric, massively increased in usage, becoming the second most popular fuel type after petrol. Purely electric fuel type started gaining more popularity in the same year, however it still remains one of the least used fuel types. The data of the year 2022 shows us that once again diesel has taken the second lead in popularity, however this data is incomplete since the year has not ended.

![image](https://user-images.githubusercontent.com/98031776/189128505-5c8915df-49e3-4ae9-9261-58efd3091ae0.png)

![image](https://user-images.githubusercontent.com/98031776/189128546-6b1423f3-b67f-4547-9092-921d69d62983.png)
![image](https://user-images.githubusercontent.com/98031776/189128578-67155c9c-829c-4fd2-9e2f-17b13ad338fd.png)
![image](https://user-images.githubusercontent.com/98031776/189128598-f77d4026-b320-4f38-b796-696d43c43c4f.png)


## Average yearly emissions
To further collaborate our initial observations, we decided to look into the emissions from different fuel types over a four year period. It was observed that the highest emissions came from  Petrol and Diesel fuel types with regards to Carbon dioxide(CO2) and Nitrous Oxide(NOx) emissions respectively. 
![image](https://user-images.githubusercontent.com/98031776/189128740-c440a9a6-3d3d-4f48-b2f1-21cb0f5f8c4e.png)

Year on year however, electric cars produced the lowest emissions of CO2 and NOx. 
![image](https://user-images.githubusercontent.com/98031776/189128785-229e5cf8-8f7f-4286-b91a-b0fb0854804c.png)

Why are we considering NOx emissions you may wonder? Research has shown that NOx — a gas that is 300 times more harmful to the climate than CO2 — is steadily increasing in the atmosphere (https://www.cbc.ca/news/science/nitrous-oxide-climate-1.5753907). A look at the charts clearly shows increasing emissions from NOx in 2022. By this project therefore we are also creating awareness about NOx emissions and its impact on our world.

## Comparing manufacturers' emissions
This investigation considered the options available to consumers, both across manufacturers and within their own ranges. First the mean for each manufacturer was calculated and these averages were plotted as a bar chart; over the bars, the standard deviation is plotted as an error interval. 

![image](https://user-images.githubusercontent.com/98031776/189127652-1ab3c96f-680a-43a9-9af3-792b40d2e407.png)


Then the range of vehicles produced by each manufacturer was plotted as a box-and-whisker diagram, each stacked on top of the other for easy comparison.

![image](https://user-images.githubusercontent.com/98031776/189127533-3e752795-433b-4cdf-9430-c307c1d86130.png)
Most manufacturers produce vehicles with a wide variety of emissions. Cars with low or zero emissions are still mostly outliers, showing there is some choice for consumers, but very little compared to the large swathe of cars between 100-200 CO2.   
In order for carbon emissions to come down, electric and hybrid cars will have to become the normal model of production, not an outlier.

## Looking ahead
This investigation involved determining the emissions of the vehicle based on the engine power, fuel type and the powertrain. These variables were plotted on regression scatter plots, boxplot and stripplots. 
![image](https://user-images.githubusercontent.com/98031776/189128847-e52612da-15ae-49bc-a725-7c358d2f9326.png)

From the boxplot it was possible to see that consumers do not have a lot of choice when choosing electric cars that have high engine power.
![image](https://user-images.githubusercontent.com/98031776/189129085-c3be337e-0959-4cda-b3a1-0a922ebc5133.png)

The regression plots show the emissions of engines based on the engine power, fuel type and powertrain. From the regression plot the CO2 emissions for all the types of vehicles analysed shows that the electric powered cars have zero emissions regardless of engine size. In contrast the internal combustion engine and hybrid electric vehicles emissions increase with increasing engine power.
![image](https://user-images.githubusercontent.com/98031776/189129126-d012bfbd-13c8-41e5-a75b-c064a92e0076.png)
![image](https://user-images.githubusercontent.com/98031776/189129147-6715d90a-5141-451e-8d81-d0386a9221d8.png)
![image](https://user-images.githubusercontent.com/98031776/189129162-6c13d0e7-4069-4d9c-a606-e895e49ab866.png)

With the stripplots it was possible to show that the internal combustion engine have a minimum of CO2  and NOx emissions that they can produce. Their emissions cannot be lowered any further. The stripplots were also used to justify the data cleanup that was done in the WLTP CO2 column.



## Conclusions

There is a limit to how clean fossil fuels can be, and even hybrid cars are not as clean as pure electric (section 6). 
The Co2, THC, and NOx emissions of vehicles is not falling fast enough(section 4).
The availability of pure electric and hybrid cars is small, but growing (sections 3 and 5)


Finally, because of the above three conclusions, and in light of the opening data regarding the contribution of internal combustion engines to climate change, moving to electric cars should be a priority. Their production and purchase should be encouraged ahead of petrol and diesel cars.

### Two caveats:
Li-Ion batteries for cars are going to be a limiting factor; governments must ensure that Lithium can be responsibly sourced [https://www.theguardian.com/news/2020/dec/08/the-curse-of-white-oil-electric-vehicles-dirty-secret-lithium].
The infrastructure to support electric cars - including large amounts of renewable electricity - must be put into place [https://www.wwf.org.uk/updates/how-do-i-charge-my-electric-car-renewable-energy]


