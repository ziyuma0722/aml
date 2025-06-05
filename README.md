# aml


## Project 1

## Project 2: Heart rhythm classification from raw ECG signals

We first used biosppy, neurokit2 and hrvanalysis to filter the ecg signals and extract features them. For each signal, we extracted the following features:
- Peaks periodicity features, i.e. mean, std, min, max, etc. of differences between successive P, Q, R, S and T peak indices;
- Peak Amplitude features, i.e. mean, std, min, max, etc. of amplitudes at the P, Q, R, S, and T peaks;
- Interval Features, i.e. mean, std, min, max, etc. of the durations of physiological intervals (PR interval, PR segment, QRS complex, ST segment, QT interval);
- Heart rate features, i.e. statistical features of the heart rate time series;
- Spectrum features in the frequency domain, i.e. the power spectral density;
- Template mean the standard deviation features, i.e. the mean the standard deviation of averaged heartbeat templates;
- Autocorrelation features, i.e. the autocorrelation of the signal clip to capture repeating patterns;
- Features from hrvanalysis to complement the above features, i.e. the time-domain, geometrical, frequency-domain, CSI-CVI, Poincare and sample entropy features.
  
After extracting the features, we did the preprocessing step by data imputation and data standardization. We also tried outlier removal, but it didn’t bring us better results. 
We also did features selection by trying to
- remove correlated features, since the features extracted before are strongly correlated, and some of them might represent similar information.
- select the best k features.

For the classification, we tried different approaches: 
- The different classifiers (with or without oversampling to overcome class imbalance), e.g. the LGBMClassifier, the HistGradientBoostingClassifier, the RandomForestClassifier, and their combinations by StackingClassifier.
- LSTM and Feed Forward Neural Networks using different architectures and activation functions to do the classification.
  
The best model is using a single LGBMClassifier or HistGradientBoostingClassifier with oversampling after removing correlated features.

