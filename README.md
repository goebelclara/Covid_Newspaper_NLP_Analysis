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
**1_Data_Preparation**:  Clean newspaper articles and parse data for recognition of political agents<br>
**2_Lexicon_Based_Models**: Conduct sentiment analysis on newspaper articles using lexicon-based models as a proof-of-concept<br>
**3_Snorkel**:  Conduct sentiment analysis via weak labelling of newspaper articles using Snorkel and an ensemble of various lexicon-, machine-learning, and deep-learning-based methods<br>
**4_ML**:  Conduct sentiment analysis on newspaper articles using machine learning methods. Such standalone models may generalize better than the Snorkel labelling functions, but this was not the case for this project<br>
**5_DL**:  Conduct sentiment analysis on newspaper articles using deep learning methods, including transfer learning, fine-tuning of pre-trained BERT models, and training a neural network from scratch. Such standalone models may generalize better than the Snorkel labelling functions, but this was not the case for this project<br>
**6_Data_Finalization**:  Prepare sentiment-labelled newspaper articles for visualization<br>
**7_Timeseries**:  Transform sentiment over time into a timeseries with smoothing<br>
**8_Topic_Model**:  Identify key topics of criticism in sentiment-labelled newspaper articles using LDA, NMF, and clustering methods<br>

## External resources used:
**Data**: Data from [SMD](https://www.smd.ch/SMDView/log/index.jsp)<br>
**Lexicons**: [SentiWS](https://wortschatz.uni-leipzig.de/de/download), [PolArt](https://aclanthology.org/W09-4635.pdf), [Emotion](https://github.com/Jana-Z/german-sentiment-lexicon), and [GERVader](https://github.com/KarstenAMF/GerVADER) lexicons<br>
**Embeddings**: [fastText](https://fasttext.cc/docs/en/crawl-vectors.html), [GloVe](https://www.deepset.ai/german-word-embeddings), [Word2Vec](https://www.deepset.ai/german-word-embeddings)<br>
**Models**: [Guhr](https://huggingface.co/oliverguhr/german-sentiment-bert), [Lüdke et al.](https://huggingface.co/mdraw/german-news-sentiment-bert), [NLPTown](https://huggingface.co/nlptown/bert-base-multilingual-uncased-sentiment), [PYABSA](https://github.com/yangheng95/PyABSA).

## Method description:
The analysis follows four main steps:<br>
**Data preparation**: Through regular expressions, mentions of various political agents are identified in the newspaper articles. These agents include politicians, political organs, institutions, and officials. Any sentences mentioning such agents are extracted. In case a sentence mentions multiple agents, the sentence is split into relevant subclauses based on a custom-defined clause class relying on the verb's position.<br>
**Sentiment analysis**: Following a proof-of-concept using unsupervised lexicon-based methods, a weak labelling approach with Snorkel is employed. A small share of sentences is annotated manually with regard to their sentiment. For the remaining sentences, the labels are generated through an ensemble of Snorkel labelling functions. These functions include unsupervised lexicon-based methods, custom-defined keyword-based methods, supervised machine learning models (e.g. XGBoost), and pre-trained BERT models (e.g. from [Lüdke et al.](https://huggingface.co/mdraw/german-news-sentiment-bert)). Thereafter, various standalone machine-learning and deep-learning-based models are tested. Such end models may generalize better than the Snorkel labelling functions, but this was not the case for this project. <br>
**Timeseries analysis**: A daily mean is taken across the sentiment labels. This irregular timeseries is smoothed with a Box kernel following [Falck et al.](https://www.uni-trier.de/fileadmin/fb2/LDV/Rettinger/publications/IPP2018_Falck.pdf) as well as a local regression for visualization purposes.<br>
**Topic modelling**: For sentences labelled to express a negative sentiment, topics of criticism are validated using non-negative matrix factorization.