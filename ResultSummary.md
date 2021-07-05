   Kettle
============


This is a project, or said "code take-home assignment," from Kettle to predict **wildfire frequency** and **severity of wildfires**.  The goal attempts to solve the questions listed below.   

1. What is the distribution of wildfires in California?
2. Is there any trend in the wildfire frequency and severity (acres burned)?
3. Is there any trend in climate?
4. What are the major factors affecting the frequency and severity of wildfires?
5. Can you build models that predict annual/monthly (1) frequency wildfires, (2) severity of wildfires (by acres burned)? The models you build should be able to showcase your knowledge and skills in machine learning and problem-solving.

To answer the question and express my logic and my coding skills, I use the Jupyter notebook for convenience. The meanings of each Jupyter notebook are described below. 

1. Kettle_Q1.ipynb:  
This notebook access the data from the sqlite3 database and extract it to only the California region. Afterward, plotting the wildfires (by size) on a GIS map to express the spatial distribution. 

2. Kettle_Q2-4.ipynb:   
This notebook attempts to answer the question 2-4. Here, I use seaborn for the visualization and use some simple climate data analysis skills to look for the pattern and compare it with El Nino 3.4 index and the Northern Pacific Oscillation index. By comparing with the El Nino index, It somehow looks like the pattern is slightly matching by comparing with the peak year, although we can see the peaks in 91-92, 97-98, 07-08, 15-16. By that, I think the pattern is slightly delayed than the event of El Nino/La Nina. But interestingly to see in advance if I can have the dataset.  

In addition, this note also contains the analysis by month or by day of a year. It is clear to see that the wildfires most likely occur during the boreal summer. The increase starts in April and reaches the peak in July, especially at the end of June and early July (day173 - day 192).  By looking at the severities of the wildfires, the highest occurrence is at class A, and the more serious events like D, E, F, G are not strong and no significant changes. One distinguished pattern of this is class B occurrence decrease since 2007, while the reduction of class A in 2008-2010 and gets back to 4000 times occurrence after 2011. The last point of this notebook is that by the cause reason figure, we can see the "Miscellaneous" and "Equipment Use" are the major reason causing the fires. 

3. Kettle_Q5-*.ipynb: 

> DL-ADAM: using a deep learning approach (Convolutional Neural Network with ADAM Optimizer) to buildup the prediction model.  
> MLP: using shallow model structure (1 input, 5 hidden, 1 output). The number of nodes within the hidden layer selection is based on the paper journal: Stathakis (2019), how many hidden layers and nodes?   
> RandomForest: using the sklearn-RandomForest module.  

Kettle_Q5-*.ipynb contains DL-ADAM, MLP, RandomForest, and RAndomForest with spatial processing based on various deep learning and machine learning models.  It is well-known the deep learning models probably will become the wrong pickup. This is because we don't have sufficient datasets to train the model (In my case, I trained models by each month. It will only give me (2015-1992+1)*12 = 288 sets dataset).  For this reason, I believe that shallow model (MLP), logistic regression, Random Forest will be the better option for us.  I still put the DL-ADAM just testing whether the Conv2D layers can handle the problem by our dataset. 

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



PS3: 

In the Gdrive, there are three folders of dataset I did use, which is **"CA shape"**, **"S_USA.MTBS_BURN_AREA_BOUNDARY"**, and **"S_USA.MTBS_FIRE_OCCURRENCE_PT"**. 
- The "CA shape" contains the geometry of the entire USA, including the Alaska. I think this is not related to the CA shape. 
- The "S_USA.MTBS_BURN_AREA_BOUNDARY" directory looks useful by directory name, but **.shp** is missing. Cannot read the dataset.
- The S_USA.MTBS_FIRE_OCCURRENCE_PT directory is not using since I start to use "FPA_FOD_20170508.sqlite". 
