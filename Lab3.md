# Lab 3
## Google Cloud Fundamentals: Getting Started with App Engine
***

## Objectives

In this hands-on Lab, we create and deploy a simple [App Engine](https://cloud.google.com/appengine) application using 
Googl Cloud shell

**The Following Tasks will be performend to achieve above objectives**
    
* Intialize App Engine

* Preview an App Engine application running locally in Cloud Shell

* Deploy an App Engine  application for that others can reahc it

* Disable an App Engine application  when you nolonger need it.


## Tasks 
***

### Task 1 - Initialize App engine

1. In the Cloud Shell, Initialize App Engine with your project and Choose a region

    `gcloud app create --project=$DEVSHELl_PROJECT_ID`

    
    > when prompted, select the region in the Lab such as us-central1

2. Clone the source for sample application in the **hello_world** directory

    `git clone https://github.org/GoogleCloudPlatform/python-docs-samples`

3. navigate to the source directory

    `cd python-docs-samples/appengine/standard_python3/hello_world`

### Task 2 - Run Hello World  Application locally

1. At the Cloud Shell Prompt, run this command:

    `audo apt-get update`

2. Setup environment in which to run the application using python virtual environments

    `sudo apgt-get install virtualenv`
    
    > if prompted [Y/n], press `Y` and then `Enter`

    `virtualenv -p python3 venv`
    
3. Activate th enew virtual environment like this

    `source venv/bin/activate`

4. Install dependencies; this must be done within your project directory

    `pip install -r requirements.txt`

5. Run the Application

    `python main.py`

    >Ignore any warnings 

6. Preview the Application by Clicking on **Web Preview > Preview on port 8080**

    >To access **Web Preview** icon, collapse the navigation menu

7. End the Test by typing **Ctrl+C** in the Cloud Shell.

8.  Notic that in the  Cloud Console Dashboard, no application is deployed.

### Task 3 - Deploy and run Hello World on App Engine

1. Naviagte to source directory

`cd ~/python-docs-samples/appengine/standard_python3/hello_world`

2. deploy the Application

    `gcloud app deploy`

    >Incase you are prompted, Press `Y` then `Enter`

3. Launch Browser to preview App at http://YOUR_PROJECT_ID.appspot.com 

    `gcloud app browser`

    >Replace **PROJECT_ID** with the actual project ID in your Cloud Shell

4.Copy and paste the url into a browser window to view App Content.

<<<<<<< HEAD
=======

### Task 4 - Disable App Engine
>>>>>>> develop
