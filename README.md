# Steps for installing dependencies and running a Rasa Chatbot for an AI Testing Tool.

**Link to github :** https://github.com/angeln5/rasa_project

---

## Directory: 

    .
    |-- .gitignore  
    |-- config.yml  
    |-- credentials.yml  
    |-- domain.yml  
    |-- endpoints.yml  
    |-- index.html  
    |-- style.css  
    |-- actions
        |-- actions.py  
        |-- __init__.py
        |
        |-- __pycache__
    |-- data
        |-- nlu.yml
        |-- rules.yml
        |-- stories.yml
    |-- Images
    |-- models
        |-- README.md
    |-- results
        |-- augmented_intent_confusion_matrix.png
        |-- augmented_intent_errors.json
        |-- augmented_intent_histogram.png
        |-- augmented_intent_report.json
        |-- non_augmented_intent_confusion_matrix.png
        |-- non_augmented_intent_histogram.png
    |-- tests
        |-- test_stories.yml
    |-- train_test_split
        |-- nlg_test_data.yml
        |-- nlg_training_data.yml
        |-- test_data.yml
        |-- training_data.yml

## Installations:

1. Download Visual C++ executable (this is a tensorflow dependency) & install it.

    [Link to downloads]( https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0 
    "Visual C++ Downloads")

2. Download Anaconda graphical installer & install it.

    [Link to anaconda installer](https://www.anaconda.com/products/individual#windows "Conda installers")

3. Open the Anaconda prompt after running it.

    **The following steps should be done in the Anaconda prompt.**

4. Go to the directory where the project is stored (`cd` into that folder.)

5. Create a new environment to install Rasa Open Source into.

    1. Type in the command

        _python==3.7 specifies the version of python that is used for this project_


        > conda create --name name_of_environment python==3.7

    2. When prompted, type the follow to allow installion

        > yes

    - Step 5 only needs to be done whenever you want to create a new environment since the same environment can be used for multiple projects.

6. Activate the conda environment.

    1. Type in the command
    
        > conda activate name_of_environment
    
    2. (base) changing to (name_of_environment) means that you're now working in your activated environment.

    - This step must be done every time you are starting your bot
    
7. Install dependencies and Rasa open source:

    1. Type in the following:

        > conda install ujson

        > conda install tensorflow

        > pip install rasa

    - Step 7 only needs to be done once for each conda environment

8. Train the chatbot.

    1. Type in: 

        > rasa train

    - This step can take awhile

9. To run the bot on the command line.

    1. Type in:

        > rasa shell

    2. To stop the shell, type in:

        > /stop

**The following steps (still in Anaconda prompt) will allow running the bot with the user interface.**

10. Install dependencies by typing in:

    > pip install python-engineio==3.13.2

    > pip install python-socketio==4.6.1

11. To run the rasa server with the UI.

    1. Type in:

    > rasa run -m models --enable-api --cors "*" --debug

    2. Go to the project folder, right click on the index.html file and open it on an internet browser.

        - Team had issues when using Internet Explorer Browser

    3. Click on the message icon at the lower right corner of the page to open up the messaging prompt.

    4. Make sure that in the index.html file, socketUrl is set to the correct link.

        - Example:

            - On the Anaconda prompt (when the rasa server is running):

                `Starting Rasa server on http://localhost:5050`

            - Then the socketUrl (in index.html) should be (line 65):

                `socketUrl: "http://localhost:5050",`
---

## How to run the  model
There are two models currently located in this directory.

`model_final.tar.gz` This is the latest model which should be used to communicate with the chatbot. 

`model_nlu_split.tar.gz` This model was only trained using training data when an 80/20 nlu split was performed in order to split the data into training data and testing data. The testing and training data can be found in the [train_test_split](../train_test_split) directory.

---

#### Choosing which model to run.
In order to initialize a session with the chatbot, run the following command:
```bash
rasa shell -m .\models\model_final.tar.gz
```
This will use the latest model. You can also use the other model by changing the name of the model when you run the command. 

## License and copyright

© Maya Halabi, Julio Mercado Soto, Angel Nguyen, San Jose State University
