# 💓 Heart Rate Data using ECG and PPG Devices

This repository contains **Heart Rate (HR)** data collected from a cohort of healthy elderly individuals (age 60+). The data was gathered in 15-minute sessions with participants at rest (seated with arm support), using simultaneously a **Photoplethysmography (PPG)** and a **Electrocardiogram (ECG)** device.

## 🩺 Devices Used
- **Fitbit Inspire HR**: A wrist-worn PPG device.
- **Polar H10**: An ECG chest strap.

> **Note**: Polar H10 is recommended for accurate HRV measurements in non-clinical settings due to its strong correlation with traditional ECG methods. Several studies support its accuracy:
> - [Study on Polar H10 accuracy](https://actavia.e-coretvasa.cz/pdfs/cor/2022/04/06.pdf)
> - [Validation of Polar H10 for HRV analysis](https://pubmed.ncbi.nlm.nih.gov/36081005/)

## 📊 Data Collection and Processing
- **Polar H10 Data**: Extracted using the Elite HRV app, this dataset includes **raw RR intervals** (time between successive heartbeats), also known as IBI (Interbeat Interval). RR intervals were converted to HR using the formula [`HR = 60000 / IBI`](https://www.researchgate.net/publication/232219445_Instantaneous_heart_rates_and_other_techniques_introducing_errors_in_the_calculation_of_heart_rate).
- **Fitbit Inspire Raw HR Data**: Captured concurrently with the Polar H10 data, enabling a direct comparison between PPG and ECG.

## 📁 Repository Contents
- **Raw and Processed Data**: Includes original RR intervals from Polar H10 and HR data from both devices.
- **Code for Fitbit Data interpolation**: The HR data acquired through Fitbit consists of a time series that presents gaps (missing data) due to possible measurement failures, To mitigate the inaccuracy of PPG sensors, which may be caused by a number of [different factors](https://www.mdpi.com/2079-6374/11/4/126) (e.g., skin tone, obesity, age, gender, respiration, venous pulsation, body temperature, motion artifacts, and ambient light). In order to guarantee the integrity of the data, it is necessary to fill in those gaps. To ensure data was filled in the best way, I tested several different conventional time series imputation methods. In order to measure the performance of each approach, missing values were randomly introduced to a complete time series, obtained from Polar H10 and filled in with the different methods comparing the predicted results with the original values. The best technique according to the Root Mean Square Error (RMSE) was PCHIP, as depicted below.

  ![image](https://github.com/user-attachments/assets/a8e55e25-504e-461a-aa6f-a45267de6577)

 >**Note**: This dataset was used as part of my master's thesis research. More information can be found in the published paper: [HRV Monitoring Using Commercial Wearable Devices as a Health Indicator for Older Persons during the Pandemic](https://www.mdpi.com/1424-8220/22/5/2001).
