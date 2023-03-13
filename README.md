# Algorithmic trading with Machine Learning.
This notebook uses a two machine learning models that train on two simple moving averages to predict whether a stock should be bought or sold to make a profit. The machine learning models used are a support vector classifier (SVC) and a random forest classifier. Results are plotted against the returns from holding the stock.

## Technologies
This notebook runs on a jupyter notebook.
The program uses the pandas, matplotlib, and sklearn libraries.

## Installation Guide
Install python 3.7.15 and open machine_learning_trading_bot.ipynb using jupyter lab, ensuring that the emerging_markets_ohlcv.csv file containing the data is in the Resources folder.

To install the latest version of sklearn use the following command:

pip install -U scikit-learn

To install the latest version of matplotlib use the following command:

python -m pip install -U matplotlib

Pandas can be installed by downloading the Anaconda python distribution and following the installation instructions.

## Usage
The code runs directly in the jupyter notebook. Data are first read from the csv file, then percent returns are calculated. Simple moving averages are calculated using 4 and 100 period windows. Buy and sell signals are generated when the price is respectively increasing or decreasing. Returns are generated to create a baseline model.

The data are split between training and testing, where the first three months are used to train the machine learning models and the rest of the days are predicted on. The training data is then scaled and the models are fit to it. Predictions are then generated, as well as classification reports. Returns from each strategy are plotted against the baseline strategy as well.

## Results

### Model tuning 
The SVC model was first trained on three months of data to obtain a baseline. The returns were plotted against actual returns from holding the stock in the following plot:
[!SVC_Returns.PNG]
The model was then retrained on six months of data to see if the returns could be improved.
[!SVC_Returns_6_months.PNG]
Training on six months of data yielded 30% higher returns!

The short SMA window was also modified from 4 days to 50 days to see if returns would improve and the results are plotted below
[!SVC_Returns_50dSMA.PNG]
Now the model is underperforming, so the short window was kept at 4 days,
Modifying the short SMA window did not improve results, but the increased number of training days was maintained at 6 months.

### Model Comparison
The returns from each of the models compared to the actual returns are plotted below:

[!RF_Returns.PNG]
[!SVC_Returns.PNG]

In the time period selected, only the support vector classifier strategy outperformed the baseline. The SVC model's returns follows the baseline's closely when compared to the returns from the random forest classifier. The random forest classifier seems to perform better when the stock price is falling when compared to the SVC.

The classification reports can also provide insight into the differences between the two models.

The classification report for the random forest model is below:
[!RF_classification_report.PNG]
And the classification report for the SVC model is as follows:
[!SVM_classification_report.PNG]

The accuracy of the models was 49% for the random forest and 56% for the support vector classifier, indicating that the random forest model performs worse overall. Despite the worse overall performance, the random forest model is much better than the SVC model at predicting when the price will fall with much higher recall and precision for the short signals, at the cost of worse performance when predicting buy signals. 

## Contributors

By Brian Wander
brianwander101@gmail.com
www.linkedin.com/in/brian-wander

---

## License

MIT license.
