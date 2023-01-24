# sentiment_analysis
Project description (explain EXACTLY what the code is doing):

- The main purpose of this project is to be able to predict sentiment of a give tweet (sentiment analysis). The project first takes in a dataset, consisting of tweet text and labels (negative, neutral, positive), and then drops any existing null values. The data is then split using train_test_split() method, first to split the data into main & test and then used a second time to split the main data into train and validation. BERT was used to create a lookup table that represents tweets using two steps: preprocessing and encoding. The pre-processing and encoding steps added the special tokens to each tweet text (CLS and SEP), assigned unique ids for each word, created embedded vectors for each word in a sentence, and created embedded vectors for each tweet (pooled output). The neural network first takes in the tweet text as the input layer, which is then passed to the BERT pre-processor and then to the BERT encoder, resulting in pooled outputs. For the first method, the pooled output is passed through three layers: dropout, dense (ÔreluÕ), dense (ÔsoftmaxÕ). The dropout layer helps prevent over-fitting and optimizes the network. The pooled output first feeds into the dropout layer, the output of which is fed into dense (ÔreluÕ) layer. The output of the first dense layer, is then fed into the second dense (ÔsoftmaxÕ) layer. For the second method, there is an additional Bi-LSTM layer before the dropout layer. The project then uses ÔadamÕ optimizer and Ôcategorical_crossentropyÕ loss function. Since the data for this project had three labels, the categorical crossentropy loss function and softmax was used. The model is then trained with the training and validation data and then finally evaluated on the testing data. Accuracy was used as a means to compare the two models. 


Installation instructions:
1. Please download the code file titled Òfinal_sentiment_analysis.ipynbÓ from github link: https://github.com/kaurj7/NLP/tree/main/Sentiment%20Analysis 
2. Sign in to your gmail account. 
3. Open google colab through the following link: https://colab.research.google.com
4. Once you have followed the link above, you should see a screen with an upload option on the top right.
5. Click on the ÒUploadÓ tab on the top right. You should now see the screen with an option to choose file to upload.
6. Click on ÒChoose FileÓ and choose the code file downloaded earlier. 
7. Once the upload is successful, you should be able to now see the file opened in google colab, ready for use.


Usage instructions:
- Make sure you have successfully downloaded and opened the code file by following the installation steps mentioned above. 
- To be able to follow the code easier, the code file consists of several code blocks, which can be executed individually. In order to run the entire code from start to finish, please start at the beginning of the file and execute each code block in order. 
- Each code block has a ÒplayÓ button on the left, used to run that particular code block. 
- Please wait for each code block to be successfully executed (denoted by a green check mark, underneath the ÒplayÓ button), before running the next block of code.
- Repeat this process until the end of the file.  


Method:

- For this project, BERT was used for word embedding (pre-processing and encoding).  The pooled output from the BERT model was then used as input for the network layers. Within the network, there are three layers being used: dropout --> dense (ÔreluÕ) --> dense (ÔsoftmaxÕ), where the output of each layer serves as the input to the next layer. For the second method, there is an additional Bi-LSTM layer in the network. The dropout layer helped optimize the neural network. 


Data:
- The data chosen for this project was taken from Kaggle: https://www.kaggle.com/code/irasalsabila/twitter-sentiment/data. 

- Data information:
o Size: 27.5k
o Labels (3): Negative, Neutral, and Positive

- Data Split:
o Training --> 80% (consists of 22,258 instances)
o Validation --> 10% (consists of 2,748 instances)
o Testing --> 10% (consists of 2,474 instances)


Results:

- Method 1:

0 (Negative)
Precision: 0.61 
Recall: 0.55 	    
F1-score: 0.58 	   
Support: 778




1 (Neutral)
Precision: 0.57	       
Recall: 0.63              
F1-score: 0.60              
Support: 1112

2 (Positive)
Precision: 0.65	       
Recall: 0.61              
F1-score: 0.63                
Support: 858
      
Accuracy: 0.60      
Macro avg: 0.61 	      
Weighted avg: 0.61 	   



- Method 2:

0 (Negative)
Precision: 0.62 
Recall: 0.61    
F1-score: 0.62 	   
Support: 778

1 (Neutral)
Precision: 0.57	       
Recall: 0.68              
F1-score: 0.62              
Support: 1112

2 (Positive)
Precision: 0.73       
Recall: 0.56              
F1-score: 0.63                
Support: 858
      
Accuracy: 0.62      
Macro avg: 0.64 	      
Weighted avg: 0.64





Discussion:

- As seen by the results above Method 1 had an accuracy of 0.60, whereas Method 2 with Bidirectional LSTM (Bi-LSTM) performed better with an accuracy of 0.62. Due to the nature of Bi-LSTM, this was an expected result. Bi-LSTM not only added an additional layer to the previous model, but it also provided sequence information in both directions (forwards and backwards). Additionally, due to the added dropout layer (to prevent over-fitting), the validation accuracy closely resembled the test accuracy for both the models. This was also an expected result. Another interesting noted observation was that, even though the neutral class (denoted by 1 in the classification report above) had the most instances in the data, the neutral class precision was the lowest in both models. Since the data had more neutral instances than positive or negative, it was expected that the model would perform the best for the neutral class. Even though, method 2 performed better, a bigger difference in accuracy between the two models was expected. Since method 2 consisted of a bidirectional layer, it was surprising to see only a slightly improved accuracy. One reason, method 2 may not have performed as well as expected is due to the epochs and the batch size. More testing was carried out later and it was concluded that the default batch size of 32 was indeed the optimal batch size. More experimentation with different epochs was tested. There were three epochs that were used for this process: 20, 15, and 10. 20 epochs had better accuracy than 15 epochs, and 15 epochs had better accuracy than the final 10 epoch reported accuracy. However, the difference in the accuracies wasnÕt as great as expected. To better understand the process, the models should be tested with a different train/dev/test split. For instance, changing the train/dev/test split to 75%, 15%, 10% respectively, and comparing results would also help answer some questions. 



Future work:

- The main focus for this project was working with BERT model and understanding how sentiment analysis works. Due to which, not much focus was put on the data itself. The next steps would be to analyze and study the data in depth. Making observations about the data in terms of emojis and punctuation would help construct a better model in the future. Additionally, working with a different model than BERT pre-processor for tweet processing, is an interesting route to take as the next steps. By using a different model, the focus can then be shifted towards the data and emojis. A comparison study can then be performed, between the two experiments to study the impact of emojis on the model performance. Through the comparison, a higher accuracy can be achieved. Another route for the future would be to use additional layers for the network to get better results. 
 
