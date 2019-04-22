# Animal-Sound-Classifier-using-Watson-Studio
Create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

Learn how to best gather and prepare data, create and deploy models, deploy and test a signal processing application, create models with binary classifications, and display the predictions on a web page created using Node-RED. 

This repo is based on the IBM Early Program - Animal Sound project. [Here.](https://github.com/bedangSen/animal-sounds)

## Table of Content

+ [Getting Started](#getting-started)
+ [Gathering and Preparing Data](#gathering-and-preparing-data)
+ [Build a Machine Learning Model](#build-a-machine-learning-model) 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

1. Sign up for an [IBM Cloud account](https://ibm.biz/MLinSound).
   <p align="center">
    <img src="https://i.imgur.com/nkyKMAS.png" width="800"  align="middle">
   </p>
  
1. Create an instance of the Node-RED starter kit service:
    - Go to the [Node-RED starter kit](https://cloud.ibm.com/catalog/starters/node-red-starter?bss_account=525ccc0465f143be9bcc9715846ff31f) page in the IBM Cloud Catalog.
    - Log in to your IBM Cloud account.
    - Click **Create**.
    
    <p align="center">
    <img src="https://i.imgur.com/qRffJVH.gif" align="middle">
   </p>
   
1. Install and set up Python 3.
1. Install and set up Git command line.
1. Install and set up Pip.
1. Install and set up a suitable IDE to modify Python code, for example:
    - [Atom](https://atom.io/)
    - [Sublime](https://www.sublimetext.com/)
    - [VS Code](https://code.visualstudio.com/)
1. Create an account in [Kaggle](https:/www.kaggle.com)

1. Clone the repository:
   ```
   git clone https://github.com/bedangSen/Animal-Sound-Classifier-using-Watson-Studio.git  
   ```

1. Change to the new animal sounds directory:
   ```
   cd animal-sounds
   ```

1. Optional: If you have virtualenv, create a new environment for the application and then activate the environment.

   1. Find the path by running which or where commands:

      1. Windows
         ```
         where python
         ```
      1. Mac or Linux
         ```
         which python
         ```

   1. You can then use the path to create your virtual environment.
      ```
      virtualenv animals -p <path to your installed version of python> 
      ```

   1. Activate the environment:

      1. Windows
         ```
         animals/Script/activate.bat
         ```

      1. Mac or Linux
         ```
         source animals/bin/activate
         ```

## Gathering and Preparing Data

1. If you don’t already have an audio directory, create one for the audio files that you will download from Kaggle:
   ```
   mkdir audio
   ```
   
1. Sign in to Kaggle [here.](https://www.kaggle.com/mmoreaux/audio-cats-and-dogs) and download the cats_dogs.zip file. 
   
   <p align="center">
    <img src="https://i.imgur.com/EVPvKqd.png" align="middle">
   </p>
   
1. Extract the files and copy them to the audio directory. 
    
1. Change to the src directory inside the animal-sounds directory:
   ```
   cd src
   ```
   
1. Run the pip install command to install the application requirements, which are the converter and the service application that you'll use in a subsequent lab:
   ```
   pip install -r requirements.txt
   ```
   
1. Run the converter application that finds the audio files and generates a sound.csv file in the outputs folder:
   ```
   python ospconverter.py
   ```
   
1. Review the generated file.
   
   <p align="center">
    <img src="https://i.imgur.com/EVPvKqd.png" align="middle">
   </p>
   
## Build a Machine Learning Model 
   ### 1. Create a machine learning project
   <p align="center">
    <img src="https://i.imgur.com/WMwvB29.gifv" align="middle">
   </p>
   
   1. Log in to your IBM Cloud account and create an instance of the Watson Studio service.  
      1. Name your service instance. 
      1. Choose a region.
      1. Select the `lite` plan.
      1. Click `Create`. 
      
   1. Launch Watson Studio by lcikcing on `Launch Tool`. 
   
   1. 
1. 
1.
1. 
1.
