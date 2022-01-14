# ST-CCN-AQI
## 4	Experiments and Results
In this paper, the spatial range optimization method is used to select sites with strong spatial correlation, and the optimal data set is used to divide the data. The parameters such as learning rate, kernel number and data input window are optimized, so as to obtain the model with the best prediction effect and predict IAQIPM2.5 value, IAQIPM10 value and IAQINO2 value.Finally, the prediction performance of the model is compared with that of the benchmark model to draw a conclusion. RMSE, MAE and R2 are used to evaluate the advantages and disadvantages.
### 4.1	The data collection
With the rapid development of science and technology, air quality is being seriously affected by the emission of air pollutants from agriculture, industry, transportation and other activities.As the economic center of China, the current situation of air pollution in Shanghai can not be ignored. Therefore, Shanghai is selected as the research area in this paper, and the distribution of monitoring stations is shown in Fig.4 :
<div align=center>
<img src="https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github1.png"/>
</div>
<div align=center>
Figure 4: Distribution of monitoring stations in Shanghai
</div>
In this paper, hourly air quality data sets were collected from 9 monitoring stations in Shanghai from August 26 to September 28, 2013, including IAQIPM2.5, IAQIPM10, IAQINO2, temperature, pressure, humidity, wind speed and weather.Geographic location information, including longitude and latitude, was obtained for 9 monitoring stations in Shanghai. The data description is Table 1:
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github2.png)
</div>
### 4.2	Data Preprocessing
In this paper, the data set obtained is preprocessed.For single missing value, first-order Lagrangian linear interpolation (linear interpolation) is adopted. For continuous multiple missing value, data in the same period of time within the adjacent date is used to fill in, making the overall data conform to the change rule. The linear difference formula is as follows:
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github3.png)
</div>
Where (x0,y0),(x1,y1) represents the interpolation of two adjacent nodes, and epresents the inserted missing value.Different features in the dataset have different dimensional and dimensional units. In order to eliminate the dimensional influence between features, comparability between feature indexes is made.The maximum and minimum normalization method is used to limit the data within the range of [-1,1], and eliminate the influence of singular data on air quality prediction.The calculation formula of maximum and minimum normalization is as follows:
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github4.png)
</div>
Where  is the maximum value of a series of features,  is the minimum value of a series of features, and  is the final result.To further understand the data, this paper randomly selected a site as the target site, and conducted statistics and analysis of its data as shown in Table 2:
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github5.png)
</div>
As can be seen from the above table, the maximum value of IAQIPM2.5 at the target site is 181.239 with a mean value of 87.422, and the mean values of IAQIPM10 and IAQINO2 are 44.762 and 18.116, respectively, with a decrease of 48.8% and 79.6% compared with IAQIPM2.5. It can be seen that PM2.5 pollution in Shanghai is serious. PM10 and NO2 pollution is relatively light.In order to improve the air quality of Shanghai, it is urgent to predict IAQI in Shanghai.
### 4.3	The Experimental Setup
#### 4.3.1 Spatial Range Selection
Firstly, the correlation between the target site and other surrounding sites is calculated. Secondly, strong spatial sites are selected.The correlation coefficient and number of sites in different spatial ranges are different, as shown in Figure 5.The selection of spatial range directly affects the selection of input data of the model.In this case, data selection is not representative and comprehensive, leading to poor prediction effect of the model.When the spatial range with small correlation coefficient is selected, the number of stations with large spatial range is too much, and it is easy to introduce the stations with poor correlation, which makes the model prediction inaccurate.It is impossible to extract comprehensive spatial strongly correlated features based on the spatial range selected by individuals.Therefore, this paper uses the violence search method to traverse all spatial ranges including the target site, and determines the optimal spatial range by comparing various performance indicators.
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github6.png)
</div>
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github7.png)
</div>
<div align=center>
Figure 5: Mean values of correlation coefficients in different spatial ranges
</div>
The above two pictures are the distribution map and enlarged view of air monitoring stations in Shanghai.Pentagram is the target site randomly selected in this paper, and triangles in different colors represent surrounding sites.In this paper, elliptic dotted lines are used to divide different spatial ranges from near to far according to the distance between surrounding stations and target stations.In this paper, the mean values of correlation coefficients between site and target site in each spatial range are 0.933, 0.915, 0.907.0.906, 0.903, 0.884, 0.88, 0.87 from near to far.As shown in Table 3, the average correlation coefficient represents different spatial ranges to explore the influence of spatial range selection on model prediction performance.
The selection of spatial range directly affects the selection of input data of the model.In this case, data selection is not representative and comprehensive, leading to poor prediction effect of the model.When the spatial range with small correlation coefficient is selected, the number of stations with large spatial range is too much, and it is easy to introduce the stations with poor correlation, which makes the model prediction inaccurate.It is impossible to extract comprehensive spatial strongly correlated features based on the spatial range selected by individuals.Therefore, this paper uses the violence search method to traverse all spatial ranges including the target site, and determines the optimal spatial range by comparing various performance indicators.As shown in Table 3, the average correlation coefficient represents different spatial ranges to explore the influence of spatial range selection on model prediction performance.
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/github8.png)
</div>
It can be concluded from the above table that when the average correlation coefficient is 0.906, the RMSE and MAE of ST-CCN-IAQI model are 11.806 and 8.511, indicating the best prediction performance of the model.Compared with the spatial range of maximum average correlation coefficient, RMSE and MAE decreased by 12.5% and 15.3% respectively.Therefore, the sites within the spatial range marked in red in the figure above are selected as strong spatial correlation sites as the input of ST-CCN-IAQI model.
#### 4.3.2 Data Set Partitioning
After determining the input data set of the model, it is necessary to divide the data set. The prediction performance of the model is affected differently by using different proportions of data sets.In order to improve the prediction performance of ST-CCN-IAQI model, this paper divided data sets according to the sequence of training set, verification set and test set. (2:1:1), (3:1:1), (4:1:1), (5:1:1) and (6:1:1) were used as data partitioning strategies to conduct experiments successively, and the optimal partitioning strategy was selected by comparing various performance indicators. The experimental performance is shown in Table 1:
<div align=center>
Table 1 : The influence of different partition ratio on prediction performance
</div>
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/fourth.png)
</div>
As can be seen from the above table, when the data set partition ratio is (5:1:1), the ST-CCN-IAQI model achieves the optimal value of each performance indicator, RMSE is 10.468, MAE is 8.340.As the proportion of training sets increases, the prediction performance of the model is gradually optimized. However, when the proportion of training sets is too large and the proportion of verification sets is too small, it is not conducive to the air quality prediction of ST-CCN-IAQI model.Therefore, the data set partition ratio was set as (5:1:1) for subsequent experiments.

#### 4.3.3 Parameter Tuning

After the above experiments, data selection and data set division have been completed.Next, the hyperparameters of ST-CCN-IAQI model were optimized to improve the prediction accuracy of the model.In the iterative process, the learning rate will control the progress of learning, that is, the step of forward and the speed of gradient descent, thus affecting the prediction effect of the model.In this paper, the learning rate values are set as 0.1, 0.005, 0.001, 0.0005 and 0.0001 for comparative experiments. The experimental results are shown in Table 2:
<div align=center>
Table2: Model predictive performance of different learning rates
</div>
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/first.png)
</div>
As can be seen from the above table, the learning rate is 0.001,ST-CCN-IAQI model has the best prediction performance, RMSE and MAE are 11.806 and 8.511 respectively.When the learning rate is large, the length of forward progress increases, leading to inadequate learning, while when the learning rate is small, the gradient decreases and the convergence rate slows down.The size of the kernel provides input for an expansion of convolution convolution in lower layer to the upper network amount of historical data, a data input window value forecast data when the scope of historical data input, the value of these two parameters determine the input to the expansion of convolution model is the data comprehensive site is extracted by precise time correlation characteristics of the data.Therefore, the kernel size was set as 2, 3, 4, 5 and 6, and the data input window range (3~24) were respectively set as comparison experiments, and RMSE and MAE were taken as performance evaluation indexes.Experimental results are shown in Figure 3:
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/second.png)
</div>
<div align=center>
Figure 3(a) : Model prediction performance for different kernel sizes
</div>
<div align=center>
![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/third.png)
</div>
<div align=center>
Figure 3(b) : Model prediction performance of different input window values
</div>
According to the figure above, when the kernel size is 4 and the data input window size is 24, ST-CCN-IAQI model has the best prediction performance, with RMSE of 11.806, 11.807 and 9.873, respectively.When the kernel value and data input window value are small, the input historical data are local and the time correlation feature extraction is not comprehensive. When the kernel value and data input window value is large, the data with weak time correlation will be introduced, leading to the inaccurate time correlation feature extraction.The optimal parameter values were used to predict air quality in subsequent experiments to ensure the accuracy of ST-CCN-IAQI model prediction.
