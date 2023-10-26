# Title-Generator-From-Research-Paper


## Data Preparation:

Import the required libraries, including pandas and SimpleT5.
Define the file path to a JSON data file that contains text data for summarization.
Specify a chunk size for reading the JSON file in smaller portions, which is useful for efficiently processing large datasets.
Initialize an empty list called dfs to store DataFrames.

## Read and Process Data in Chunks:

The JSON file is read and processed in chunks using pd.read_json. The lines=True argument is used to treat each line in the JSON file as a separate JSON object.
Each chunk of data is extracted with only two columns: 'title' and 'abstract', which are used as the 'source_text' and 'target_text' for summarization tasks.
Each chunk is appended to the list dfs.

## Concatenate DataFrames:

After processing all the chunks, the individual DataFrames in dfs are concatenated into a single DataFrame named df.
The column names are renamed to 'source_text' and 'target_text'.

## Preprocessing Source Text:

To indicate that the 'source_text' should be summarized, "summarize: " is prepended to each text in the 'source_text' column. This is a common practice when using T5-based models for summarization.

## Data Splitting:

The dataset is split into a training set (train_df) and a test set (test_df) using the train_test_split function from scikit-learn. The split ratio is 70% for training and 30% for testing.

## Model Initialization:

An instance of the SimpleT5 model is created with the T5-base architecture.

## Model Training:

The model is trained using the training data (train_df) with the following parameters:
- source_max_token_len: Maximum token length for source text.
- target_max_token_len: Maximum token length for target text (summary).
- batch_size: Number of samples in each training batch.
- max_epochs: Number of training epochs.
- use_gpu: Indicates whether to use a GPU for training.
The model is trained to generate summaries of the input texts.

## Load Trained Model:

After training, the model is saved with a specific name.
Later, it is loaded for inference using the load_model method. The model architecture and weights are loaded to make predictions.

## Text Summarization:

A sample text (text_to_summarize) is provided for summarization.
The provided text is preprocessed by adding "summarize: " as a prefix.
The trained model's predict method is used to generate a summary for the input text. The model generates a summary of the text according to its training.
