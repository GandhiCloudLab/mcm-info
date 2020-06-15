# Runtime Data collector for Springboot application in Openshift

Here are some steps to Implement Runtime Data collector for the spring boot application in Openshift container platform.

## 1. PreRequisite

### 1.1. Obtain the hub server config info

Obtain the hub server config info using the below url. As as result you might have downloaded with `ibm-cloud-apm-dc-configpack.tar`.

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/dc_config_server_info.html


### 1.2. Downloading the J2SE data collector

Downloading the J2SE data collector using the below url. As as result you might have got  `j2se_datacollector.tgz`.

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/download_j2se_dc.html

## 2. Installing on Managed Cluster

Here are we are going to do some steps in managed cluster which are mentioned in the below kc pages.

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/dc_config_authorize.html

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/config_J2SE_dc_monitor_icp_apps.html

### 2.1. Login into managed cluster

a) Login into managed cluster using `oc login`

### 2.2. Create Namespace

We are going to deploy the app in the `fpro-icam-app-ns`. 

a) oc apply the file  `files/managed-cluster/00-namespace-app.yaml`

Note: These files are available in this repo.

### 2.3. Create icam-server-secret

a) Extract the tar file `ibm-cloud-apm-dc-configpack.tar` that was downloaded in step 1.1. 

b) Get into to the folder `ibm-cloud-apm-dc-configpack` in the commandline.

c) Copy the content of the file  `files/managed-cluster/03-icam-server-secret.sh` and run in the command line.

### 2.4 Create role and role binding

a) oc apply the file  `files/managed-cluster/01-lwdc-clusterrole.yaml`

b) oc apply the file  `files/managed-cluster/02-lwdc-rolebinding.yaml`

## 3. Building Docker Image for SpringBoot application.

Here we are going to do some steps to build docker image which are mentioned in the below kc pages.

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/config_J2SE_dc_monitor_icp_apps.html

### 3.1. Build your app

The app can be build using `maven` or `gradle`.

a) In case of maven Create some `temp` folder.

b) Copy the `j2se_datacollector.tgz` file that was downloaded in step 1.2 into the `temp` folder. 

c) Rename the springboot application jar file into `app.jar` and copy to the `temp` folder. 

d) Copy the docker file from `/files/docker/Dockerfile` into the `temp` folder. 

e) Copy the silent file from `/files/docker/silent_config_j2se_dc.txt` into the `temp` folder. 

f) Update the silent file `silent_config_j2se_dc.txt` in the `temp` folder.
    The `MAIN_CLASS` key should be substittued with your Springboot main class.

### 3.1. Copy files

a) Create some `temp` folder.

b) Copy the `j2se_datacollector.tgz` file that was downloaded in step 1.2 into the `temp` folder. 

c) Create springboot application jar.

1. Goto the root folder of the application.

2. Build the app and it creates .jar file

    Run `gradle build` , if you have gradle. 

    or

    Run `mvn clean package`, if you have maven. 

3. Rename the jar file into `app.jar`

4. Copy `app.jar`  to `temp` folder. 

d) Copy the docker file from `/files/docker/Dockerfile` into the `temp` folder. 

e) Copy the silent file from `/files/docker/silent_config_j2se_dc.txt` into the `temp` folder. 

f) Update the silent file `silent_config_j2se_dc.txt` in the `temp` folder.
    The `MAIN_CLASS` key should be substittued with your Springboot main class.

### 3.2. Build docker image

a) Goto the above `temp` folder.

b) Run `docker build ......` command to create docker image 

c) Run `docker push ......` command to push the docker image 

## 4. Deploying Springboot app in the MCM hub

Here are we are going deploy the app in MCM hub. The below kc page contains the info about it.

https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/config_J2SE_dc_monitor_icp_apps.html

### 4.1. Deploy the app

The sample deployment files with Channel and Subscriptions are available at the location `/files/hub/`

a) Replace the `<<IMAGE_NAME>>`, with the actual image that you created above, in the file `/files/hub/21-deployable-bankweb.yaml`.

b Update the managed cluster details in the file `/files/hub/30-placement.yaml`

c) oc apply to all the files available in the folder `files/hub/`

### 4.2. Access the app

a) In the managed cluster, the namespace `fpro-icam-app-ns`, should have some route created. Using the route you can access the app.

b). Create some workload and you can get to see the golden signals in the hub.

