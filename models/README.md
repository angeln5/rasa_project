## How to run the  model
There are two models currently located in this directory.

`model_final.tar.gz` This is the latest model which should be used to communicate with the chatbot. 

`model__nlu_split.tar.gz` This model was only trained using training data when an 80/20 nlu split was performed in order to split the data into training data and testing data. The testing and training data can be found in the [train_test_split](../train_test_split) directory.

#### Choosing which model to run.
In order to initialize a session with the chatbot, run the following command:
```bash
rasa shell -m .\model_final.tar.gz
```
This will use the latest model. You can also use the other model by changing the name of the model when you run the command. 
