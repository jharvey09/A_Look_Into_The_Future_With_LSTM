# A Look Into The Future With LSTM
![pexels-tara-winstead-8386440](https://user-images.githubusercontent.com/80294571/131234808-158a24ba-6e73-4a9f-9a2e-0df85aa64612.jpg)
*Photo by **_Tara Winstead_** from Pexels*

In this assignment, I will use tools such as *deep learning recurrent neural networks* to model bitcoin's closing prices. One model will use the FNG indicators to predict the closing price, and the second model will use a window of closing prices to predict the nth closing price. One example is the Crypto Fear & Greed Index (FNG)

## Preparing The Data: (Closing Predictor)
1. Set the random seed for reproducibility
2. Load *"Greed and Fear"* sentiment data for Bitcoin

![image](https://user-images.githubusercontent.com/80294571/131236988-e76c55e8-be3d-471e-8245-a0a42538ec4a.png)

3. Load historical data closing prices for Bitcoin

![image](https://user-images.githubusercontent.com/80294571/131237012-44b2e735-5d2a-42fc-aeaa-1372b44c1134.png)

4. Join data to a single DataFrame

![image](https://user-images.githubusercontent.com/80294571/131237035-1d13eddf-7df3-488c-a299-10715ed0c53e.png) - *tail*

![image](https://user-images.githubusercontent.com/80294571/131237058-46fe8980-041d-4b0a-8165-1a6eb718cc7d.png) - *head*

5. Predict Closing Prices using a window size 10 of previous closing prices. For different performance changes, use numbers from 1 - 10. For this model, I chose to use a window size of 7.
6. Use 70% of the data for training and the remaining for testing.
7. Use *MinMaxScaler* to scale data between 0 and 1
8. Reshape the features for the model


## Build and Train the LSTM RNN:
1. Build the *LSTM model*, if adding additional LSTM layers, set return sequences to True. But not neccessary for final layer
2. Compile the model
3. Summarize the model

![image](https://user-images.githubusercontent.com/80294571/131237290-2219de87-0a44-4253-9578-1954f88ebb9a.png)

4. Train the model

![image](https://user-images.githubusercontent.com/80294571/131237310-d774ae04-bb3e-444e-aa54-766acec67144.png)

## Model Performance:
1.Evaluate the model using the X_test and the y_test data

![image](https://user-images.githubusercontent.com/80294571/131237354-0e750041-07f7-4c36-97dd-9dc26e764df3.png)

2. Create a DataFrame of Real and Predicited values

![image](https://user-images.githubusercontent.com/80294571/131237383-7f066a81-4277-4440-8870-e80c7254b986.png)

3. Plot the real versus predicted value in a line chart

![image](https://user-images.githubusercontent.com/80294571/131237403-587f79d5-344f-4cac-b3a4-0e417db162b3.png)


## Fear and Greed Predictor:
1. Follow same steps above ***(Prepare Data, Build and Train the LSTM model, Model performence)***
2. summarize model, for this model I used a window size of 9

![image](https://user-images.githubusercontent.com/80294571/131237612-87096927-cfb6-40b2-a714-e7dc1aa92cf5.png)

![image](https://user-images.githubusercontent.com/80294571/131237632-9c04f4f5-b9fa-4577-87fc-a9ebc9ab8f7a.png)

![image](https://user-images.githubusercontent.com/80294571/131237643-d4db7d44-4007-479b-81af-91b6a5a01401.png)

3. Create DataFrame of Real and Predicited values

![image](https://user-images.githubusercontent.com/80294571/131237683-4aaafa20-0667-434d-98c7-4fc03d34b384.png)

4. Plot the real versus the predicited values as a line chart

![image](https://user-images.githubusercontent.com/80294571/131237723-fff69ffd-fe3d-427e-899c-632e3395e1be.png)

## Conclusion:
In preparation for these models, I arrived at three questions that would make the cohesive connection between data, predictions. First thing I asked myself was, ***"Which model would have the lowest loss?"*** Next, I compiled the information to see, ***"Which model tracks the actual values better over time?"*** I had to think the best way to figure this out was to know, ***"Which window size works the best for the model?"***

After comparing both models *(Fear and Greed Index, Closing Prices)* using a 10-day window, It would be concise in pointing out that the Closing Prices model would appear to be the better model.
*Closing Prices Loss: 0.0540 | Fear & Greed Index Loss: 0.1256*

**Elapsed Tracking Data:**

The model based on closing prices had appeared to track the "true" values better than the model based on the Fear and Greed Index. After comparing the charts for the two models displaying Real vs. Predicted values, over the elapsed time, the predictions based on the Closing Prices model reflected more of a "true" value than the model based on the Fear and Greed Index. Using a smaller window size on both models gave better predictions, but the "Closing Price" model was the closest to real or "true" value.

