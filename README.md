# ML-TASK1
Link To Dataset="https://drive.google.com/file/d/1Vb_ETboWWRIXdwZzY4N3fvAtmYULc1MC/view?usp=drive_link"
Link to Colab Notebook="https://colab.research.google.com/drive/1nwlHq1JhfiqmTqLZl6RoOL2hjidI1IJZ?usp=sharing"

Firstly to find the dataset, I searched various websites like kaggle, research papers, gov.in websites, physionet,etc. At last I found a dataset of 80 individuals on physionet, that too with tidal volume data being quite erratic and discrete, as it was ranging from negative data to as large as 10L, which might be recorded due errors or leakage in mask or exposure to outside. Also it had 80 different csv files for every subject with V_tidal as function of time. To get quite reasonable tidal volume I used different techniques, firstly as original dataframe didn't had a V_tidal column, I created that column, then used loop to read all 80 csv files and get V_tidal from it store it in respective row. To get rid of outliners in V_tidal I used quantile box technique, with quantile range between 0 to 15%ile as it gave most reasnable V_tidal, I also selected only the positive values and dropped the negative ones. After this I checked for One breath cycle to get V_tidal for one cycle, I did this by checking sudden change(decrease) in V_tidal. After this I just found the mean of different V_tidal in different breath cycles, this was the time averaged Tidal Volume of that Subject. After this 80 original datapoints were founds with corresponding V_tidal. 

To increase datasize I used these 80 points to extrapolate more data. Before this I converted the Categorial data into numerical by using "Label_Encoder". After this I added random noise to the data and did interpolation. During interpolation it was necessary that categorial having positive integer encoding is interpolated as previous format, for this I prespecified those columns with there range of integer values and then used them and passed dataframe to another function implement these changes. After this I did splitting and scaling of data.

For training I didn't used DNN as it was not giving desired results, instead I used RandomForest and Linear Regressor models.

Now to Run code I suggest to run in COLAB. To run we just need to execute blocks in sequential up to down order.





