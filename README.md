# Animal-Sound-Classifier-using-Watson-Studio
Create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

Learn how to best gather and prepare data, create and deploy models, deploy and test a signal processing application, create models with binary classifications, and display the predictions on a web page created using Node-RED. 

This repo is based on the IBM Early Program - Animal Sound project. [Here.](https://github.com/bedangSen/animal-sounds)

## Table of Content

+ [Getting Started](#getting-started)
+ [Gathering and Preparing Data](#gathering-and-preparing-data)
+ [Build a Machine Learning Model](#build-a-machine-learning-model)
+ [Create predictions in a Node-RED applicaiton ](#create-predictions-in-a-node-red-applicaiton)
+ [Conclusion](#conclusion)

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
       <img src="https://i.imgur.com/awaQ6Ma.gif" align="middle">
      </p>

   ### 3. Deploy the Machine Learning Model
   <p align="center">
             <img src="https://i.imgur.com/ozkCzZj.gif" align="middle">
         </p>            
   
   1. Click `Deployments`.
   1. On the right side of the page, click `Add Deployment`.
   1. Give the deployment a name (and optional description), select `Web service`, and then click `Save`.
   1. Wait for the model to deploy. The status will show DEPLOY_SUCCESS when it is complete. If it fails to deploy, try refreshing the browser after a few minutes. Alternatively, delete that deployment and follow these steps again.
   1. Click the name of the deployment.
      1. note the `deployment ID`.

## Create predictions in a Node-RED applicaiton 
   ### 1. Predict the animal sound
   1. Log in to [IBM Cloud](https://ibm.biz/MLinSound).
   
   1. If you haven’t created an instance of Node-RED, create one:
      <p align="center">
       <img src="https://i.imgur.com/KWgg8L5.gif" align="middle">
      </p>
   
      1. In IBM Cloud, click Catalog > Starter Kits > Node-RED Starter.
      1. Enter an application name and domain.      
         > The application name must be unique because it will be publicly addressable. Most likely the name catsdogs is already taken. The domain for this application does not need to match the domain that you used for Watson Studio.
      
      1. Click `Create`. It might take some time for your instance to be created and started.
         <p align="center">
          <img src="https://i.imgur.com/GwfsBrs.gif" align="middle">
         </p>
      
      1. After your instance of Node-RED is running, click `Visit App URL`.
      1. Optional: Secure your Node-RED instance with a user name and password.
      1. Click `Next` and `Next` again to complete the setup. Then, click `Go to your Node-RED flow editor`.
      
   1. Log in in to your Node-RED instance by using the credentials that you previously specified.   
      > Next, you will be importing a prebuilt flow into your Node-RED instance. This flow will allow you to upload a file and run it through the machine learning model that you created earlier.
      <p align="center">
       <img src="https://i.imgur.com/CjZh8wO.gif" align="middle">
      </p>   
   
   1. Open a new tab and go to the GitHub repositoryand select the `noderedflows` folder.
      1. Select the `predictionflow.json` file.
      1. Click `Raw` and copy the file contents to your clipboard. 
         > By clicking `Raw`, you can copy the raw data without having any unnecessary data on the clipboard that will result in errors when pasting.
      
   1. Back in your Node-RED instance, click the menu icon and click `Import > Clipboard`.
      1. Paste your clipboard contents into the field and click `Import`.
         > You might see a number of unknown nodes that appear in the imported flow. This is because the Node-RED starter kit comes preinstalled only with certain nodes. You will install the additional nodes in the next steps.
      
   1. Click the menu and click `Manage palette`. Then, select the `Install` tab.
      <p align="center">
       <img src="" align="middle">
      </p>
      
      1. Search for `node-red-contrib-watson-machine-learning`.
      1. Click `Install`. Then, click `Install` again to confirm the installation.
      1. Install two more nodes: `node-red-contrib-browser-utils`, which contains a microphone, and `node-red-node-base64`. The flow should now show all nodes.
   1. Click Deploy. Ignore any warnings about the new nodes. You will configure those nodes in the next few steps.
      > Your application is now deployed and is ready for you to test. Before experimenting with an audio file, you will start with a hardcoded test to check that the prediction is working.
   
   1. Initiate the flow by using the blue tab on the left of the `Hard Coded Test node`.
      1. Click the `Debug` tab. Depending on your version of Node-RED, you might need to click the Debug icon to show the debug messages pane.
         > You should see a "No Configuration Found" error message. This occurs because the Watson Machine Learning node (Run Prediction) has not been configured.
   
   1. Double-click the machine learning node (Run Prediction).
      1. Click the Pencil icon to edit the WML Connection configuration. Then, complete the configuration by using your machine learning credentials. The Access Key can be any non-empty value.
      1. To find your credentials, select the service from IBM Cloud and click `Credentials`. If your machine learning credentials don’t include an access key, then enter dummy text into that field. Then, click `Update` when you're done.
      1. Refetch the Model List.
         > This will temporarily hide the mode and deployments fields because the node invokes Watson Machine Learning APIs to retrieve a revised list. After the new lists are retrieved, the fields will reappear. Depending on network latency, this might a while to complete. If the fields are not displayed, click Done, click Deploy, and open the node again.   
      1. Set the mode to `Run Prediction`. Then, select your model and deployment.
      1. Click `Done` to save the configuration and deploy the updated flow.
      
   1. Initiate the flow by clicking the left tab.

   
   ### 2. Deploy and test the signal processing 
   1. Open a terminal window and create or navigate to a directory for the application.
   1. Navigate to animals-sounds/src directory.
   1. Edit the ospservice.py
      <p align="center">
       <img src="https://i.imgur.com/SQNWkkd.png" align="middle">
      </p>
      
      1. Change the host name so that it is unique in the `manifest.yaml` file.
      1. Save your changes. 
   
   1. Log in to the IBM Cloud CLI if you aren't already:
      ```
      ibmcloud login
      ```
      > If you are using a federated account, login using `ibmcloud login --sso`
      
   1. From the command line, push your application to IBM Cloud:
      ```
      ibmcloud push
      ```
      > If the ibmcloud command doesn’t work, try cf push.
      
      After your application is running, you can access the test web page from a web browser:
      `https://<your-host-name>.mybluemix.net/audio`     
      
   1. Click either `Upload` or `Perform OSP` to select an audio file from the sounds directory in your project on your local machine.
      1. If you see a series of numbers, your application is running, and the API is ready to use in your Node-RED flow.
   
   ### 3. Run predictions against the audio files
   
   1. Open your Node-RED flow
   1. Double-click the Perform OSP HTTP Request node.
   1. Change the URL to https://<your-host-name>.mybluemix.net/audio/nodered. Then, deploy your changes.
   1. Use either the microphone node or the file inject node to initiate the flow. Unless you have a cat or dog around, it’s probably better to use the file inject node.
   1. Check the output to verify the results.
  
  
## Conclusion

You now have an application that takes audio tracks as input and processes a signal from the audio file to obtain a series of numbers that it uses to make a machine learning-based prediction as to whether the sound is from a cat or a dog.

You can expand the components that you developed in this repository to other sound-based machine learning models.
