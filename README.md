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
    <img src="https://i.imgur.com/T6AtOug.png" align="middle">
   </p>
   
## Build a Machine Learning Model 
   ### 1. Create a machine learning project
  
   1. Log in to your IBM Cloud account and create an instance of the Watson Studio service.  
      <p align="center">
       <img src="https://i.imgur.com/WMwvB29.gif" align="middle">
      </p>
   
      1. Name your service instance. 
      1. Choose a region.
      1. Select the `lite` plan.
      1. Click `Create`. 
      
   1. Launch Watson Studio by clicking on `Get Started`.   
   
   1. From the home page and click `Create a New Project`. 
      <p align="center">
       <img src="https://i.imgur.com/zmh8EQc.gif" align="middle">
      </p>
      
      1. Select `Data Science` 
      1. Give the project a name and description.
      1. Make sure that the Storage field is populated with cloud-object-storage credentials.
         1. If your Storage field is showing as unpopulated, click `Cloud Object Storage`.
         1. Click `Add` to add Cloud Object Storage for Watson Studio.
         1. You might need to go back to the previous step to associate the cloud object storage with your data science project.
         1. When you're done creating the project, click `Create`.
   ### 2. Create a machine learning model
   
   1. Create a Watson Machine Learning Model
      <p align="center">
       <img src="https://i.imgur.com/AqSojMp.gif" align="middle">
      </p>
      
      1. Click on `Assets`
      1. Click Add to project and select the Watson Machine Learning asset type.
      1. Name the model and optionally provide a description.
      1. Select the project that you created and click `Associate a Machine Learning service instance`.
      1. If you do not have a service, select the appropriate plan and click `Create`. If you already have a service, click `Existing` and select it from the list.
      1. Select `Model Builder` because you want the system to do this for you.
      1. Associate an Apache Spark instance. Similar to connecting the Machine Learning service, click `Associate an IBM Analytics` for Apache Spark instance.
      1. If you have an existing service, go to the `Existing` tab and select the service. If you need to create a service, follow the instructions in the New tab.
      1. Click `Reload`.
      1. Select `Manual` so that you can prepare the data and select the models yourself.
      1. Click on `Create`. 
   
   1. In the Select Data Asset page, click `Add Data Assets`.
      <p align="center">
       <img src="https://i.imgur.com/i1bR2fM.gif" align="middle">
      </p>
      
      1. Click `Load` and browse for the cats and dogs CSV file. On a Mac, it's the soundmac.csv file.
      1. Select the file that you just uploaded in the main page. You might need to refresh the page to see the file. Then, click `Next`.
      
   1. Train the model. 
      <p align="center">
       <img src="https://i.imgur.com/i1bR2fM.gif" align="middle">
      </p>
   
      1. Select `COLUMN1` from the Column value to predict menu. For Feature columns, you can decide which columns to use. For this project leave it as `All (default)` because all the remaining columns are significant.

      1. Select `Binary Classification` because you are building a model that is for cats and dogs only.

      1. Leave the validation split at 60, 20, 20. This will use 60% of the data to train the models, 20% to test the models, and 20% as a check of the better performing models to detect overfitting.
      1. On the right side of the page, click Add `Estimators`.
      1. Select all available estimators. By selecting all of them, you can see which model gives the best results for the data set. Click `Add`. Then, click `Next`.
   1. Analyze the Performance, Area under roc curve, and Area under pr curve columns. Select the model with the best performance and highest scoring curve columns. Then, click `Save`.
   
      <p align="center">
       <img src="" align="middle">
      </p>

   ### 3. Deploy the Machine Learning Model
   
   1. Click `Deployments`.
   1. On the right side of the page, click `Add Deployment`.
   1. Give the deployment a name (and optional description), select `Web service`, and then click `Save`.
   1. Wait for the model to deploy. The status will show DEPLOY_SUCCESS when it is complete. If it fails to deploy, try refreshing the browser after a few minutes. Alternatively, delete that deployment and follow these steps again.
   1. Click the name of the deployment.
      1. note the `deployment ID`.
