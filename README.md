# Fish ECG Anomaly Detection

1. ECG signal preprocessing: ECG signals collected from the devices may not ideal to classify directly because of noise from various reasons. Thus, noise need to be removed by a solution such as Butterworth BandPass Filter and signals will be normalized to a range [-1, 1].
2. R-R interval extraction: ECG signals continues to be extracted R-R intervals. This could be performed by applying Pan-Tompkins algorithm, which is used to detect the Q-R-S complex from initial ECG signals and then determine the R peaks.
3. R-R interval normalization: R-R intervals usually have different lengths (for instance, ranging 600ms to 1200ms), which could really affects the final results of ECG classification. Hence, all of the R-R intervals in will be normalized to a specific length by applying linear interpolation.
4. AutoEncoder (AE) for dimension reduction: Dataset is now the set of sequential R-R intervals and the dimension of each interval could be large. With huge datasets, it will not be efficient because of the high cost. Thus, we need to apply the AE model to reduce the data dimension before feeding them through the classification model without losing the information.
5. Classification model: This step is a combination of Deep Recurrent Neural Networks - Long Short-Term Memory (LSTM) with Fully Connected (FC) layers to handle sequential input data and classify anomalies. 
