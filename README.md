# Stock-price-prediction
Stock price prediction using LSTM
The development of the model to predict stock price involves 5 major steps:

1) Data Collection And Preparation  
Data was collected from the targeted website i.e. www.finance.yahoo.com. 
Different stock price information of international companies were collected which 
include open price, close price, maximum price, minimum price over different 
series of years. For that, we first did web scraping using python and using streamlit 
we describe the collected data. We chose closing price for the prediction.
 
2) Analyzing Using Moving Average  
For the analysis of up trend and down trend of closing price for the analyst or any 
user, we plotted the two different types of moving averages, one was 100 days 
moving average and another was 200 days moving average.

3) Preparing training and test data  
With time series data, the sequence of values is important. A simple method that we 
can use is to split the ordered dataset into train and test data sets. For the splitting 
of data, we had used pandas ‘DataFrame()’ function which separates the data into 
the training datasets with 70% of the observations that we used to train our model, 
leaving the remaining 30% for testing the model and validating the result each. 
4) Data scaling  
Most neural network architectures benefit from scaling the inputs (sometimes also 
the output) because most common activation functions of the network’s neurons 
such as tanh or sigmoid are defined on the [-1, 1] or [0, 1] interval respectively. 
LSTMs are sensitive to the scale of the input data, specifically when the sigmoid 
(default) or tanh activation functions are used. It can be a good practice to rescale 
the data to the range of 0-to-1, also called normalizing. We easily normalized the 
dataset using the MinMaxScaler preprocessing class from the scikit-learn library.
 
5) Constructing Neural Network Model  
After having defined the placeholders, variables, initializers, cost functions and 
optimizers of the network, the model is trained. Usually, this was done by further 
dividing training data set. We had divided the data set in X and Y. X had used 100 
days data and we got 101th data for Y. At this point the placeholders X and Y come 
into play. They stored the input X and target data Y and presented them to the 
network as inputs and targets. A sampled data batch of X flows through the network 
until it reaches the output layer. There, Tensor flow compares the models 
predictions against the actual observed targets Y in the current batch. Afterwards, 
Tensorflow conducts an optimization step and updates the networks parameters, 
corresponding to the selected learning scheme. After having updated the weights 
and biases, the next batch was sampled and the process was repeated itself. The 
procedure continues until all batches have been presented to the network. One full 
sweep over all batches is called an epoch. For this project, we had used maximum 
epoch of 50 for training the model. The training of the network stops once the 
maximum number of epochs was reached or another stopping criterion defined by 
the user applies. The model quickly learns the shape and location of the time series 
in the test data and was able to produce an accurate prediction after some epochs. 
Then the network model was saved for reuse. For the construction of neural 
network, we had used the keras library consisting of sequential model and LSTM, 
Dropout and Dense layer. Our LSTM model was composed of a sequential input 
layer followed by 4 LSTM layers and 4 dropout layers with relu activation and then 
finally a dense output layer with linear activation function.

Output Visualization  
Output from neural network was scaled due to the MinMax scaler , which was used 
to fit data set into LSTM model which was not the actual stock price. To get the 
actual stock price data in predicted set, we had multipliped the 1/scaled factor to the 
predicted data set. Then, we visualized the original data vs predicted data of closing 
price using matplotlib. 
