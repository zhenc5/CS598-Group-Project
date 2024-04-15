# CS598-Group-Project
Implementation Steps:
1. Download the MIMIC-III dataset
2. Extract and preprocess data in MIMIC-III by running MIMIC-Extract
3. Extract first 24 hour time-series features
4. Select clinical notes based on criteria from MIMIC-III notes
5. Preprocess clinical notes
6. Extract medical entities from clinical notes using med7
7. Convert medical entities into word representations with different embeddings
8. Create time-series data to feed through GRU/LSTM
9. Run time-series baseline model to predict 4 different clinical tasks
10. Run multimodal baseline mode to predict 4 different clinical tasks
11. Run proposed model to predict 4 different clinical tasks
12. Compare performance metrics between different models
