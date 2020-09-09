# Lab 2 
## Google Cloud Fundamentals : Getting Started with GKE


## Objectives

In this Lab, we shall leanr how to Perform the following Tasks

1. Provision a [Kubernetes](https://kubernets.io) cluster using [Kubernetes Engine](https://cloud.google.com/container-engine) 
2. Depl0y and Manage [Docker](https://www.docker.com/) Containers using `kubectl`


## Tasks To Perform

### Task 1: Start a Kubernetes Cluster
1. Place your provisioned zone into an environment variable called **MY_ZONE** as follows:

        `export MY_ZONE=us-central-1a`

2. Create a Cluster for Web servers called ***mywebfrontend*** with 2 Nodes:

        `kubectl container clusters create mywebfrontend --zone $MY_ZONE --num-node 2`
    
    Give it about 2 minutes to setup

3. Check Installed version of Kubernetes using the command below:

        `kubectl version`


### Task 2: Run & Deploy a container

1. Using Cloud Shell prompt, launch a Single instance  of the nginx container
    
    `kubectl create deploy nginx --image=nginx:1.17.10`

2. View the Pods created

    `kubectl get pods`

3. Allow web access of the nginx pod to internet and set it as Load Balancer

    `  kubectl expose deployment nginx --port 80 --type LoadBalancer `

4. Check Running Services to confirm pod is exposed and set as Load Balancer:

    ` kubectl get services `

    Take note of the External IP address displayed. 

5. Type this External IP address in your web browser. You should get the default nginx page.

6. Scale Up the number of pods :

    `kubectl scale deployment nginx --replicas 3 `

7. Confirm the new pods were added:

    `kubectl get pods`

8. Confirm the IP address has not changed

    `kubectl get services `


9. Verify the nginx webserver is still running by going ot web browser and refresh the web page from 5 above.

10. Exit the Command Line `exit`


