  California Wildfire EDA and Prediction
===========================================
California WildFire Exploratory Data Analysis and Prediction using ML/DL.

### Project  

This is a Kettle project to predict **wildfire frequency** and **severity of wildfires**.  
The goal attempts to solve the questions listed below.

### Questions   

1. What is the distribution of wildfires in California?  
2. Is there any trend in the wildfire frequency and severity (acres burned)?  
3. Is there any trend in climate?  
4. What are the major factors affecting the frequency and severity of wildfires?  
5. Build models that predict annual/monthly (1) frequency wildfires, (2) severity of wildfires (by acres burned)?   


### Results   

1. Q1.ipynb:  
- Access the wildfire data (can obtain from Kaggle, see bottom link) that is in sqlite3 database format   
- Extract info specific for California    
- Plot the wildfire and present the spatial distribution on a map    

[Code Skills: sqlite3, pandas, cartopy, numpy]

2. Q2-4.ipynb:  
-  Access the wildfire data   
-  Seaborn for visualization   
-  Perform simple statistics analysis to look for patterns in time (daily, monthly, annualy)  


3. Q5-*.ipynb:  
-  Predict the monthly sevirity frequency of wildfire      
-     
-  * Deep Learning Model: Conv2D (modified a shorten version of VGG-16/Fire Net). [one of the dimension does not have enough amount of elements to perform the entire network structure]  
-  * MLP/Shallow Model     
-  * Random Forest     

Overall,  

| | MLP| RF | RF-AVE|  
|--|-- | -- | --|  
| MAE | 26.4925 | 21.5793 | 22.16334 |  
| MSE | 4093.7791 | 2892.7273 | 3135.1573 |  
| RMSE| 63.9826 | 53.7841 | 55.9925 |  

where  
MLP    : Shallow Model  
RF     : Random Forest  
RF-AVE : Random Forest - Spatial Pattern Average      


PS1: The prediction output (plots) can be seen in each notebook.  
PS2: The annual frequency/occurance prediction can be obtained by sum of monthly prediction.  


Data Sources:   
* weather data (from NOAA, cannot share)  
* [wildfire data] (https://www.kaggle.com/rtatman/188-million-us-wildfires/metadata)  
