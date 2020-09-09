# Lab 1 
# Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives
In this lab , we shall learn how to do the following:
    * Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console
    * Create a Compute Engine virtual machine using the gcloud command-line interface.
    * Connect between the two instances


## Task 1: Create a Virtual machine **'my-vm-1'** using the command line
1. In the Top Right toolbar, Open the Cloud Shell Button
2. Click **Continue** to launch the Cloud Shell in the browser.
3. Display and Take Note of the Zone which has bene assigned to you using command below:

    `gcloud compute zones list  | grep us-central1-b`

4. To Create the virtual machine called **'my-vm-1'** , execute the code below:

    ```
    gcloud compute instances create "my-vm-1" \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-v20200902" \
    --subnet "default" \
    --tags http
    ``` 

5. Allow fire-wall ruls to allow http port using commands below:

    ` gcloud compute firewall-rules create allow-http --action=ALLOW --destination=INGRESS --rules=http:80 --target-tags=http `
5. Exit the Cloud Shell by typing  `exit`



## Task 2: Create a another virtual machine **'my-vm-2'** using the gcloud command line
1. In the Top Right toolbar, Open the Cloud Shell Button
2. Click **Continue** to launch the Cloud Shell in the browser.
3. Display a List of Zones in the region assigned to you  using the command below;

  ` gcloud compute zones list  | grep us-central1-b `

4. Set your Default Zone to **us-central1-b** using the command below

 ` gcloud config set cmompute/zone us-central1-b `



 ## Task 3 - Connect the two VM Instances 

 1. Check if the newly created Instance my-vm-2 can connect to my-vm-1 using the ping command:

 `ping my-vm-1`

 Notice the output will reveal the complete hostname of the my-vm-1 instance similar to **my-vm-1.c.PROJECT_ID.internal**

 2. Abort the command using **CTRL + C**

 3. Now use ssh to open a command prompt on my-vm-1 like so:

 `ssh my-vm-1`

When prompted about an unknown host, enter **yes** to confirm your do.

 4. Lets install nginx web server on my-vm-1 using the command below:

 ` sudo apt-get install nginx-light -y `

 5. using **nano**, we can enter some custome messages on the server home page; execut the command below:

 ` sudo nano /var/www//html/index.nginx-debian.html`

 6. Use the Arrow keys to mov edown to the line with **h1** header. Add TEXT to replace YOUR_NAME with your name.

`Hi from EMMANUEL WACHA`

7. To save your Edited file, press **Ctrl + O** and then exit nano with **Ctrl + X**

8. Confirm the web server is working. Execute this command:

`curl http://localhost`

The Response should be the page with the custome text from 6. above. 

9. Exit the Command Prompt on my-vm-1 

`exit`

You will return to my-vm-2 command prompt.

10. Let's comfirm that my-vm-2 can reach server my-vm-1, execute the command below:

`curl http://my-vm-1/`

The response will be the HTML custom message from

