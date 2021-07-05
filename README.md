# Algorithmic Trading Machine Learning Model

## Evaluation Report

This report will evaluate the algorithmic trading performance, first, based on a support vector machine (**SVM**) learning model.
We get the following **classification report** for the baseline performance of the SVM model:

              precision    recall  f1-score   support

        -1.0       0.43      0.04      0.07      1804
         1.0       0.56      0.96      0.71      2288

    accuracy                           0.55      4092
 
We get the following plot when comparing the actual vs. strategy/predicted returns:

![original_training_model](https://user-images.githubusercontent.com/80929342/124428652-d6108c00-dd21-11eb-9ba0-d8a3e530b77b.png)

We see that it has a very high recall score for the 1 values, but not so well in the -1 values.
The precision is also not desirable for both the 1 and -1 values.

##  Tuning the Model

We will then tune the model by adjusting a couple of parameters.
The first adjustment made was to change the adjust the training offset period.
For this test, we change the training offset period from 3 months to 6 months.

We get the following **classification report** for this adjustment:

              precision    recall  f1-score   support

        -1.0       0.44      0.02      0.04      1732
         1.0       0.56      0.98      0.71      2211

    accuracy                           0.56      3943

We then plot the actual vs. strategy/predicted returns for this adjustment:

![adjusted_training_period](https://user-images.githubusercontent.com/80929342/124429172-62bb4a00-dd22-11eb-9d10-866d5c13cd39.png)

The second adjustment that was made to the machine learning model was to change the short window and long window periods.
We get the following **classification report** for this adjustment:

              precision    recall  f1-score   support

        -1.0       0.52      0.03      0.05      1791
         1.0       0.56      0.98      0.71      2278

    accuracy                           0.56      4069

We also get the following plot for the actual vs. strategy/predicted returns for this adjustment:

![adjusted_short_long_window](https://user-images.githubusercontent.com/80929342/124429325-96966f80-dd22-11eb-895d-b87e5563c40c.png)

Looking at the overall results, we see that the adjustments do slightly improve the recall scores of the 1 values, but still does poorly on the -1 recall values.
Precision does increase, and it seems that changing the short/long window periods provided the best results so far.

## Using a Different Classifier

We now try using a different classifier model for the algorithmic trading to run/train on.
For this, I have decided to go with the **Logistic Regression** model.

We get the following **classification report** for the Logistic Regression model here:

              precision    recall  f1-score   support

        -1.0       0.47      0.13      0.20      1791
         1.0       0.56      0.88      0.69      2278

    accuracy                           0.55      4069

We also get the following plot for the actual vs. strategy/predicted returns:

![lr_model](https://user-images.githubusercontent.com/80929342/124429704-0a387c80-dd23-11eb-8023-e54fd51d3f53.png)

## Conclusion

After looking at the various classification reports and plots, it seems that model where the short/long window periods did the best in actually coming close to the actual returns it predicted.  The Logistic Regression model does better in the recall value for the -1, which is where all the other scenarios did poorly in.  If we were to stick with the Logistic Regression model, while also increasing the short/long windows, we might get a much better result.  However, for the machine learning scenarios that have been tested, increasing the short/long windows result in the more accurate predicted returns.
