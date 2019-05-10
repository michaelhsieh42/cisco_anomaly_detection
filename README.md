# Predictive Maintenance using Deep Learning
40 relevant attributes out of 85 were identified to be used as input to a recurrent neural network. We trained a baseline model that would “detect” anomalous events on each node as soon as they occur with a 10-fold cross validated AUC of 0.97. 

| #  | Traffic load | No. Anomalies | Duration | Description                        |
|----|--------------|---------------|----------|------------------------------------|
| 0  | 0            | 0             | 1h       | Baseline (no amolies)              |
| 1  | 500Gbps      | 0             | 1h       | Baseline (no anomalies)            |
| 2  | 1Tbps        | 11            | 1h       | BGP Clear                          |
| 3  | 1Tbps        | 8             | 0.55h    | BGP Clear                          |
| 4  | 1Tbps        | 5             | 0.72h    | Port Flap                          |
| 5  | 1Tbps        | 12            | 2h       | BGP Clear                          |
| 6  | 0            | 12            | 2h       | BGP Clear                          |
| 7  | 0            | 130           | 72h      | (VIRL) BGP Clear                   |
| 8  | 0            | 238           | 262h     | (VIRL) BGP Clear                   |
| 9  | 2.9Tbps      | 5             | .75h     | Port Admin Shut                    |
| 10 | 2Tbps        | 5             | .55h     | Port Transceiver Pull and Reinsert |

Data source: [Cisco real-world telemetry anomaly dataset](https://github.com/cisco-ie/telemetry) which includes timeseries of 85 signals from 12 nodes under 0 to 1Tbps traffic of Blue Ray/Youtube4K movie streaming, skype video calls and other activities. BGP Clear events from dataset 2, 3, 5, 6 are used for modeling for this work.

There are three notebooks in this repository:

- [Exploratory Analysis](./cisco_telemetry_eda_20190326.ipynb)
- [Data Preprocessing](./cisco_telemetry_data_preprocessing_20190401.ipynb)
- [Modeling](./cisco_telemetry_rnn_modeling_20190401.ipynb)

The preprocessed data is available in [here in s3](https://s3.amazonaws.com/cisco-anomaly-detection/preprocessed_20190401.pkl). Implementation and training was performed on an AWS EC2 p2.xlarge instance.


