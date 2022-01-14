# ST-CCN-AQI
#### 4.3.2 Data Set Partitioning
After determining the input data set of the model, it is necessary to divide the data set. The prediction performance of the model is affected differently by using different proportions of data sets.In order to improve the prediction performance of ST-CCN-IAQI model, this paper divided data sets according to the sequence of training set, verification set and test set. (2:1:1), (3:1:1), (4:1:1), (5:1:1) and (6:1:1) were used as data partitioning strategies to conduct experiments successively, and the optimal partitioning strategy was selected by comparing various performance indicators. The experimental performance is shown in Table 1:

Table 1 : The influence of different partition ratio on prediction performance

![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/fourth.png)

As can be seen from the above table, when the data set partition ratio is (5:1:1), the ST-CCN-IAQI model achieves the optimal value of each performance indicator, RMSE is 10.468, MAE is 8.340.As the proportion of training sets increases, the prediction performance of the model is gradually optimized. However, when the proportion of training sets is too large and the proportion of verification sets is too small, it is not conducive to the air quality prediction of ST-CCN-IAQI model.Therefore, the data set partition ratio was set as (5:1:1) for subsequent experiments.

#### 4.3.3 Parameter Tuning

After the above experiments, data selection and data set division have been completed.Next, the hyperparameters of ST-CCN-IAQI model were optimized to improve the prediction accuracy of the model.In the iterative process, the learning rate will control the progress of learning, that is, the step of forward and the speed of gradient descent, thus affecting the prediction effect of the model.In this paper, the learning rate values are set as 0.1, 0.005, 0.001, 0.0005 and 0.0001 for comparative experiments. The experimental results are shown in Table 2:

Table2: Model predictive performance of different learning rates

![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/first.png)

As can be seen from the above table, the learning rate is 0.001,ST-CCN-IAQI model has the best prediction performance, RMSE and MAE are 11.806 and 8.511 respectively.When the learning rate is large, the length of forward progress increases, leading to inadequate learning, while when the learning rate is small, the gradient decreases and the convergence rate slows down.The size of the kernel provides input for an expansion of convolution convolution in lower layer to the upper network amount of historical data, a data input window value forecast data when the scope of historical data input, the value of these two parameters determine the input to the expansion of convolution model is the data comprehensive site is extracted by precise time correlation characteristics of the data.Therefore, the kernel size was set as 2, 3, 4, 5 and 6, and the data input window range (3~24) were respectively set as comparison experiments, and RMSE and MAE were taken as performance evaluation indexes.Experimental results are shown in Figure 3:

![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/second.png)

Figure 3(a) : Model prediction performance for different kernel sizes

![image](https://github.com/lauysche/ST-CCN-AQI/blob/main/images/third.png)

Figure 3(b) : Model prediction performance of different input window values

According to the figure above, when the kernel size is 4 and the data input window size is 24, ST-CCN-IAQI model has the best prediction performance, with RMSE of 11.806, 11.807 and 9.873, respectively.When the kernel value and data input window value are small, the input historical data are local and the time correlation feature extraction is not comprehensive. When the kernel value and data input window value is large, the data with weak time correlation will be introduced, leading to the inaccurate time correlation feature extraction.The optimal parameter values were used to predict air quality in subsequent experiments to ensure the accuracy of ST-CCN-IAQI model prediction.
