# PPG-BP-Estimation-using-CNN-BiLSTM
This project implements a CNN–BiLSTM–Attention network for estimating systolic and diastolic blood pressure from PPG signals. The model was trained on preprocessed PPG–ABP datasets (MIMIC-II database) and evaluated on >2000 patient recordings.
Preprocessing 
The following preprocessing steps were applied before model training:
Patient filtering: Removed patients with recording durations less than 8 minutes. Removed patients with SBP values > 200 mmHg. 
Signal preprocessing: Applied a 4th-order high-pass Butterworth filter with a 1 Hz cutoff to the PPG signal to remove baseline wander.  
Windowing and target extraction: Created 8.192-second windows (corresponding to 1024 samples at 125 Hz). For each window, systolic (SBP) and diastolic (DBP) values were computed as the mean of detected ABP peaks and valleys, respectively. These averaged values were used as targets for the corresponding PPG window.
Model Architecture 
Input: 1D PPG signal window (8.162 s). 
Feature extractor: Convolutional layers (CNN) to capture morphological features. 
Temporal modelling: Bidirectional LSTM layers to learn temporal dependencies. 
Attention mechanism: To emphasise salient time regions relevant to blood pressure estimation. 
Output: Estimated SBP and DBP values.
Results 
Achieved MAE = 2.22 mmHg (SBP) and 1.5 mmHg (DBP) on patients with recording time > 8 minutes. Corresponding R² > 0.9 for long-duration recordings. Model performance degrades on recordings shorter than 8 minutes, showing MAE ≈ 15 mmHg (SBP) and 7 mmHg (DBP).

Dataset link: https://archive.ics.uci.edu/static/public/340/cuff+less+blood+pressure+estimation.zip
