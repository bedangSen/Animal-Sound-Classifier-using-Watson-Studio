# Animal-Sound-Classifier-using-Watson-Studio
Create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

Learn how to best gather and prepare data, create and deploy models, deploy and test a signal processing application, create models with binary classifications, and display the predictions on a web page created using Node-RED. 

This repo is based on the IBM Early Program - Animal Sound project. [Here.](https://github.com/bedangSen/animal-sounds)

## Table of Content

+ [Getting Started](#getting-started)
+ [Gathering and Preparing Data](#gathering-and-preparing-data)
+ [Configuring the Application](#configuring-the-application) 
+ [Running VoiceSens locally](#running-locally)
+ [Demo Screenshots](#demo)
+ [Key Components](#built-with)
+ [References (Further Reading)](#references)
+ [Future Additions](#to-do)

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

