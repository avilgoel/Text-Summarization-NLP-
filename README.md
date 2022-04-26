*Aim: *
To make a working model of any application in Natural Language Processing.  

*Project Description: *
We have developed a Text-Summarizer in Python. This is based on extractive text summarization, in which only the most important phrases and lines from the original text are found and picked. These extracted phrases or sentences are combined to make up our summary.       

*Preprocessing:*
Before starting the Text-summarization process, we found the need to clean the original text data and remove any kind of noisy, unproductive text necessary. This is because in real-life, human-written text or phrases contain various special symbols, emojis, and short words, which do not provide any useful information for natural language processing.
Our pre-processing of the original text includes :
1. Removing punctuations such as period, comma, apostrophe, quotation, question, exclamation, etc. 
2. Spacing between words and sentences is made uniform. 
3. Removing special characters like { ~, !, @, #, $, %, ^, &, *, (, ), }
4. Removing single letter words { a-z }
5. Removing digits { 0-9 }

*Workflow:*
1. Firstly, the input text to be summarized is read from the document input.txt, which can be of arbitrary size according to user needs. 
2. Sentence tokenization of the input text is done using Natural Language ToolKit (NLTK). This is followed by word tokenization (through NLTK), after which stopword removal is performed, along with a few other minor lexical operations. 
3. While using the N-Gram model, we have chosen the value of N to be 3, i.e., trigram, keeping in mind the trade-off between the context provided and the amount of computation to be done. Then, using the tokenized words, the trigram phrases have been generated for the given text.  
4. In this project, we have used the TF-IDF weighing scheme, which assigns each of the given terms in a document a weight based on its term frequency (TF) and inverse document frequency (IDF). The terms with higher weight scores are considered to be more important. 
5. We have then calculated the TF-IDF matrix for the given text, which contains the TF*IDF score of each word in a sentence. 
6. Then, the Cosine similarity values for each pair of sentences are found using the TF*IDF score in the matrix, and the average is computed for each sentence. 
7. The top K sentences based on the average cosine similarity have been taken, and we procure their sentence indices. The value of K can be set depending upon the size of the final summary desired. In our case, we have taken K to be 0.3 or 30 percent of the original text. 
8. The indices of the selected sentence have then been sorted in ascending order, the sentences corresponding to the indices are taken from the list of tokenized sentences, and these sentences are then put into the summary document summary.txt. 

*Results: *
To evaluate the performance of the summarizer, the ROUGE (Recall-Oriented Understudy for Gisting Evaluation) set of metrics has been used. It is generally used for evaluating automatic summarization of texts as well as machine translations. 
1. ROUGE-N measures the number of matching ‘n-grams’ between our model-generated text and a ‘reference’. 
2. ROUGE-L measures the longest common subsequence (LCS) between our model output and reference, i.e., it counts the longest sequence of tokens that are shared between both. 
3. The get_scores method in python returns three metrics, ROUGE-N using a unigram (ROUGE-1) and a bigram (ROUGE-2) and ROUGE-L. For each of these, we receive the F1 score f, precision p, and recall r.
4. The generated summary is compared with the original text and depending on the content of the article that is input, the accuracy obtained ranges from 55 percent to 80 percent, which is fairly good for an extractive summarizer.                    
