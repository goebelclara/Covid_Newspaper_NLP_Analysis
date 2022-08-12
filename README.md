# Covid_Newspaper_NLP_Analysis
Data journalistic investigation of the sentiment surrounding Swiss politicians, institutions, officials, and parties throughout the Covid-19 pandemic

## Project description:
This project is a data-journalistic investigation. Its aim is to assess the sentiment and key topics of criticism surrounding Swiss politicians, institutions, officials, and parties throughout the Covid-19 pandemic, based on newspaper articles.<br>

## Data source:
The data underlying the newspaper analysis stems from the Swiss Media Database, which collects and digitizes all articles written by established Swiss newspapers. A query for articles between January 2020 and April 2022, where Covid-19 was a topic in the headline or subheading, returned 87’000 articles from German-language newspapers.<br>

## Included files: 
#### Folders:
**Inputs**: Contains files which list all political agents and media. These function as inputs to the various IPYNB notebooks<br>
**Notebooks**: Contains IPYNB notebooks. This is where the data processing and analysis takes place<br>

#### IPYNB files (Notebooks folder):
**1_Data_Preparation**:  Clean newspaper articles and parse data for entity recognition<br>
**2_Lexicon_Based_Models**: Conduct sentiment analysis on newspaper articles using lexicon-based models as a proof-of-concept<br>
**3_Snorkel**:  Conduct sentiment analysis via weak labelling of newspaper articles using Snorkel and an ensemble of various lexicon-, machine-learning, and deep-learning-based methods<br>
**4_ML**:  Conduct sentiment analysis on newspaper articles using machine learning methods. Such standalone models may generalize better than the Snorkel labelling functions, but this was not the case for this project<br>
**5_DL**:  Conduct sentiment analysis on newspaper articles using deep learning methods, including transfer learning, fine-tuning of pre-trained BERT models, and training a neural network from scratch. Such standalone models may generalize better than the Snorkel labelling functions, but this was not the case for this project<br>
**6_Data_Finalization**:  Prepare sentiment-labelled newspaper articles for visualization<br>
**7_Timeseries**:  Transform sentiment over time into a timeseries with smoothing<br>
**8_Topic_Model**:  Identify key topics of criticism in sentiment-labelled newspaper articles using LDA, NMF, and clustering methods<br>

## External resources used:
**Data**: Data from SMD<br>
**Lexicons**: SentiWS, PolArt, Emotion, and GERVader lexicons<br>
**Embeddings**: fastText, GloVe, Word2Vec<br>

## Method description:
TBA