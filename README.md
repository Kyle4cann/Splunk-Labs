# Splunk Labs 1 – Step-by-Step Guide

### Introduction:
This hands-on lab is designed to walk through a complete setup and integration of Splunk within a cloud-based environment. By leveraging AWS infrastructure and Ubuntu, the lab demonstrates how to install, configure, and utilize Splunk Enterprise for real-time data indexing, analysis, and visualization. It also covers the configuration of a universal forwarder and integration with AWS S3 buckets for extended data onboarding capabilities.

### Objectives:
To create an AWS instance, install Splunk on Ubuntu, configure Splunk users, index and search static data, use SPL (Splunk Processing Language), install and configure a universal forwarder, and integrate AWS S3 bucket data with Splunk.

## Part 1: Create an AWS Account and Instance

### Step 1. 
- Open https://aws.amazon.com/console/ in your browser
- Click on the account and the AWS management console
- Click on Create a new AWS Account
- Fill in: Root user email address and AWS account name, and click verify email address
- Open your mail to verify your account

### Step 2.
- Open https://aws.amazon.com/console/ in your browser
- Click on the account AWS management console
- Click on Sign in using root user email
- Enter your Email, the characters given to you, click on I'm not a robot, and enter your  password to log in
### Step 3:
- At the search button, type ES2 and click on Instances
- Click on Launch an instance:
- Enter, fill out, or configure your server
- ### Notes:
- - Enter Name: `KyleTech`
  - Select Ubuntu under Application and OS Image: Slpunk is very compatible with Ubuntu because it is liter
  - For Splunk to run smoothly, it requires a minimum of `2 gig Virtual CPU` and `4 GB of Memory`. So, select `T3 medium`
  - Click Key Pair to create Key Pair (SplunkTest )
  - Under Security Group, select Allow All.
  - Change storage to 30 GB because you are  eligible to use up to 30 GB
- Now click on Launch instance to create an   Instance Called (KyleTech)
### Step 4:
- Check the Instance Box and click on connect
- ### Note:
  It will redirect you to a terminal page.

![image](https://github.com/user-attachments/assets/a0eead7b-e6ae-42b9-b235-ff91cd0fd7cd)
Screenshot 1.

![image](https://github.com/user-attachments/assets/0c588114-09ec-453b-bef0-7b4b18fcffc5)
Screenshot 2.

![image](https://github.com/user-attachments/assets/7950b198-024f-44e7-b61e-a674c4a60aff)
Screenshot 3.

![image](https://github.com/user-attachments/assets/25f83a11-ed78-485b-af0f-3d1a9e1e5440)
Screenshot 4.

![image](https://github.com/user-attachments/assets/b80bf878-1d7d-44a5-9415-55668e360fc4)
Screenshot 5.

![image](https://github.com/user-attachments/assets/9af73564-4b6c-4e46-8826-43fd8bbba8a2)
Screenshot 6.

## Part 2: Installing Splunk on Ubuntu Server Created on AWS

### Step 1.
- Open https://www.splunk.com/ in any browser
- Click on Products
- Free Trials and Downloads
- Click on Splunk Enterprise (Get My Free Trial)
- Create an account to download free
- Choose Your Preferred OS thats Linux
- Copy .deb link: wget -O splunk-9.4.2-e9664af3d956-linux-amd64.deb "https://download.splunk.com/products/splunk/releases/9.4.2/linux/splunk-9.4.2-e9664af3d956-linux-amd64.deb"

### Step 2.
- Go back to you Ubuntu Server to install Splunl
- ### Terminal Commands:
  ```
  Sudo su
  ( To root user)
  cd /opt
  ( To the Directory of Splunk installation)
  Copy and paste the link
  ```
  ls ( To View file downloader to the Director)
  dpkg -i splunk-9.4.2-e9664af3d956-linux-amd64.deb (To extract files to splunt default folder)
  ```
  sudo su splunk
  ```
  (to move root to Splunk directory)
  ```
  cd splunk/bin
  ./splunk start --accept-license --answer-yes
  ```
  * Enter Username: `admin`
  * Enter Password: `password`
  * We will get our IP: as http://172.31.21.104:8000
 
 ### Step 3. Allowing Port
 1. Go to AWS under Instance created and copy the Public ip address paste in your url as shown: `3.17.109.107:8000`
  - #### Note:
    Its will not connect because in setting up our instance, we only allowed 3 ports and splunk runs on port number: `8000`
2. Click on Instance Name
3. Security, Security Group, Open link in new tab, Edith `Inbond Rules Add Rules`, `Custom IP 8000`, and allowing forward enter `0.0.0.0/0` , Change Custom TCT to `All Trafic` for study purpose
4. Click Save Rules
5. Now we go back to refresh our splunk login page:

![image](https://github.com/user-attachments/assets/3e22abbe-a1a5-4f48-8243-f5f81d684046)
Screenshot  1.

![image](https://github.com/user-attachments/assets/c4212ba4-bd25-4032-9050-b76750b2ecde)
Screenshot 2.

![image](https://github.com/user-attachments/assets/91205965-035c-4679-a90a-34d631917964)
Screenshot 3.

![image](https://github.com/user-attachments/assets/5d6346ac-5a39-4149-a2da-2b64d10d82ce)
Screenshot 4.

![image](https://github.com/user-attachments/assets/0ee250cd-7c26-4755-a522-a83b2e3be86e)
Screenshot 5.

### Allowing Port

![image](https://github.com/user-attachments/assets/695c081c-53c5-432c-be92-d19747126df9)
Screenshot 1

![image](https://github.com/user-attachments/assets/f68f5efb-8608-4e38-ad00-6ded01412a36)
Screenshot 2.

![image](https://github.com/user-attachments/assets/ef9c80e7-5ef2-4772-af28-b92764ae7224)
Screenshot 3.

![image](https://github.com/user-attachments/assets/e9e38d3b-7ffa-4fdc-a575-74ff820628f1)
Screenshot 4.

![image](https://github.com/user-attachments/assets/0ee250cd-7c26-4755-a522-a83b2e3be86e)
Screenshot 5.

![image](https://github.com/user-attachments/assets/1c25bfb0-554e-4832-a158-2341fac70818)
Screenshot 6. Splunk HomePage



## Part 3: Creating User in Splunk
### Step 1
- Lick on Settings and go to Users
- Click New Users and Fill out the Form
- Name and Password
- Check Power under Assign Roles and click the arrow between Available and Selected items
- check Require password change and click Create
- Now logout from Admin and login with new user name and password (You will be Prompt to change password.

![image](https://github.com/user-attachments/assets/feae1ed2-f188-48e2-8c27-352dc2ed35b5)
Screenshot 1.

![image](https://github.com/user-attachments/assets/749b6639-cd0b-4009-9653-abf60f136c0f)
Screenshot 2.

![image](https://github.com/user-attachments/assets/cca727fa-3b9d-429e-a61f-dd9d99b48f07)
Screenshot 3.

![image](https://github.com/user-attachments/assets/cfe9de8f-0c27-463e-a86e-e762c762b927)
Screenshot 4.

![image](https://github.com/user-attachments/assets/47ab79df-cffd-4b7c-b078-8584cac8434f)
Screenshot 5.

![image](https://github.com/user-attachments/assets/0858b7e9-9fc6-443b-8a65-adf68f2d34cb)
Screenshot 6.

![image](https://github.com/user-attachments/assets/ce20799d-665a-46e7-921b-96001ef32ec3)

Screenshot 7.

### Part 4. Indexing Static Data And Searching.
### Step 1. Download CSV File
- Open any Browser go to google and search CSV file download
- Select `toolsfairy` and `Download CSV file`
### Step 2 Add Downloaded CSV File (Select Source)
- Login to Splunk Home Page
- Click on Add data
- Click on Upload
- Select File `Sample-CSV-file`
- Click Open to load file
- ### Note: Under Set Source Type
- If Timestamp is not showing Enable by:
- - Click on Timestamp
  - Select  Current and Save
- ### Under Input Settings
- Click on Create a new index
- Name it `Splunkdemo` and Save
- Select `Splunkdemo`
- Review and Submit
### Step 3. Searching
- Click on Start Searching
- In New Search type `index="Splunkdemo"` to load `Static File`
- Select All time set time to preferred time frame and press Enter to search


![image](https://github.com/user-attachments/assets/342a4336-b04d-4992-814f-4a5019b0d176)
Screenshot 1.

![image](https://github.com/user-attachments/assets/6d581f00-e112-4157-91f5-f2d61eae23e9)
Screenshot 2.

![image](https://github.com/user-attachments/assets/96c1b5ea-878d-4ebc-8f55-16a7c6cdc541)
Screenshot 3.

![image](https://github.com/user-attachments/assets/01cea488-65f7-4394-b201-5d2353ff2604)
Screenshot 4.

![image](https://github.com/user-attachments/assets/528977d1-03af-4a5f-b322-d8a26d01f43c)
Screenshot 5.

![image](https://github.com/user-attachments/assets/869d1c74-48b5-4284-8690-894e2e1c14c4)
Screenshot 6.

![image](https://github.com/user-attachments/assets/915031a8-6346-467a-81ef-a1c11be2f670)
Screenshot 7.

![image](https://github.com/user-attachments/assets/cd640d5e-aeda-4bc4-8f7d-d262ba1e85fd)
Screenshot 8.

![image](https://github.com/user-attachments/assets/48b761c2-51e5-4c07-a0f5-7e5ed471d26d)
Screenshot 9.

![image](https://github.com/user-attachments/assets/2f4857c8-35ba-42e8-a39d-ac061c9a2a61)
Screenshot 10

![image](https://github.com/user-attachments/assets/b0b47c40-6479-46ad-8760-5e2c2a51482c)
Screenshot 11

![image](https://github.com/user-attachments/assets/96e6a32c-6aa0-4e3e-88e6-83d108f3164e)
Screenshot 12

![image](https://github.com/user-attachments/assets/0fdc27b6-9bdc-4134-a496-0902c2a84120)
Screenshot 13

![image](https://github.com/user-attachments/assets/844ddbbd-e033-4514-ab4f-d1d205cee2d4)
Screenshot 14

![image](https://github.com/user-attachments/assets/07271876-0072-44e7-a2c5-808643d3482a)
Screenshot 15

![image](https://github.com/user-attachments/assets/e1fa8818-3490-465e-97bd-576dc241f59b)
Screenshot 16

### Part 5: SPL (Splunk Processing Language)
SPL: Splunk Processing Language is used to search and retrieve stored data (Playing around with Fields and creating Visualization)
### Step 1. Adding to the Index
- Under Search type `index= index` name eg `index="_internal"`
- Add Host IP
- Add Source (Matrix)
- Add Source Type (Splunkd)
### Step 2. Modify timestamp
This enhances searching 
- Earliest Field `(earliest= -15m@m)`, this means that I want to search data for the first 15 minutes
- Latest Field `(latest= -1m@m)` Mean search data for last minute
### Step 3. Graphs
- Stats convert to Table
- Chart Convert to Graph on X and Y Axis
- Time Chart converted to a graph on Time Note: before transforming, you will need PY (|) followed by command, eg,
  ```spl
  index="_internal"
  index="_internal" | stats count by sourcetype
  index="_internal" | chart count by source
  index="_internal" | timechart count
  ```
### Step 4. Creating Dashboard
- Click Edit from the homepage
- Add Panel
- Select preferred Chart
- Copy and paste the Search History and click Add Dashboard

![image](https://github.com/user-attachments/assets/07ea85df-4398-44cf-9281-e7d2f9226073)
Screenshot 1.

![image](https://github.com/user-attachments/assets/1d5b0e8b-018d-4022-baac-6acf1fa98dc2)
Screenshot 2.

![image](https://github.com/user-attachments/assets/067bdc29-c082-4e17-8abc-1fdc50e7f656)
Screenshot 3.

![image](https://github.com/user-attachments/assets/d6e26efc-92d4-4ee3-bd19-9c4d41a14090)
Screenshot 4.

![image](https://github.com/user-attachments/assets/357b5497-0c38-4553-a8ff-4646503ee3c7)
Screenshot 5.

![image](https://github.com/user-attachments/assets/b01644f5-488f-4eed-9fae-fc63bcd7343a)
Screenshot 6.

![image](https://github.com/user-attachments/assets/c7da3c3f-476a-4719-b60b-31fd701b9d6f)
Screenshot 7.

![image](https://github.com/user-attachments/assets/a6771375-29c9-4758-bddd-b1d0c5923f5c)
Screenshot 8.

![image](https://github.com/user-attachments/assets/ae8c94cf-3b0e-4a5a-906d-96f9aef70cb9)
Screenshot 9.

## Part 6: HANDLING DATA AND CONCEPTS OF BASIC FORWARDING
#### Splunk Forwarder is an agent installed on a server to capture or monitor certain files (log files)
- Data Input: What file to monitor
- Data Parsing: Converting Unstructured and Semi-structured data into a structured format.
- Data Indexing: Storing or ingeting data.
- Data Searching: Visualising Data

### Step 1. How to Install Splunk Forwarder
### Note: 
Install a universal Forwarder on another server and make sure the Splunk service is running. 
- In this case, follow Part 1, step 3 to step 4.
- Visit the Splunk webpage and click on Get My Free Download under Universal Forwarder
- Select Linux 64-bit, .deb, and copy the  link
 


### Step 1a. Commads
 ```bash
  sudo su
  cd /opt
  wget [forwarder link]
  dpkg -i splunkforwarder.deb
  cd splunkforwarder/bin
  ./splunk start --accept-license --answer-yes
  ```
  In case there is an error, run these commands:
  ```
  sudo systemctl daemon-reload
  sudo systemctl restart splunkforwarder. service
  ```
  ```
  ./restart.
  ```

![image](https://github.com/user-attachments/assets/2cb9d198-1bf3-4459-bc08-7e68917b629f)

![image](https://github.com/user-attachments/assets/ddbee8bc-b18f-4646-b236-64cc552bb224)

![image](https://github.com/user-attachments/assets/72314c5b-fb93-4328-8f28-eee7cb534aa5)

![image](https://github.com/user-attachments/assets/fcca27e9-a9e5-4d8b-b73c-06902ef4bebb)

![image](https://github.com/user-attachments/assets/4d3634ea-afd9-44d2-8f86-fc725d61941b)

![image](https://github.com/user-attachments/assets/7dfe5353-6ff9-4394-ac59-5f7cabe319c9)

### Step 2. Create/Configure Inputs:
Create an `inputs.conf` file to monitor the file (This will help Splunk to understand what file Splunk needs to monitor 
command:
```bash
cd /var/log
ls -la
cd /opt/splunkforwarder/etc/apps/search
ls -la
cd /opt/splunkforwarder/etc/apps/search/local create input in local
mkdir local
```
```bash
mkdir /opt/splunkforwarder/etc/apps/search/local
vi inputs.conf
[monitor:///var/log/syslog]
disabled = 0
index = splunkdemo2
```
 To edit, press i to `insert`, and to save `:wq enter`
  - Note: Create index name `Splunkdemo2`. Log in to Splunk as Admin, `Settings`, `New Index` and fill out form by giving it only a Name `Splunkdemo2` Save.

![image](https://github.com/user-attachments/assets/725a0434-d897-4734-8fd2-50bb4aa9f6fd)

![image](https://github.com/user-attachments/assets/3dd77093-6b10-47ae-9a88-704f0ada11fd)

![image](https://github.com/user-attachments/assets/94da4c1c-b2e0-4b6f-9f9c-4e4af82a1db1)

![image](https://github.com/user-attachments/assets/2b17e7fe-d55a-4f85-adb8-d8c1cb4431b7)

![image](https://github.com/user-attachments/assets/ed517624-b2ad-4c71-8aa6-6fc71a414b97)

![image](https://github.com/user-attachments/assets/c5e2dc11-e0f7-474c-90de-148c0d8e3e0b)

### Step 3. Create/Configure Outputs:
Create inputs.conf This will help Splunk to understand where to send data. now we have to tell our forwarder to send our capture data.
```bash
vi outputs.conf
[tcpout]
defaultGroup = my_indexers

[tcpout:my_indexers]
server = [Your-Splunk-IP]:9997
```

* Enable receiving on port `9997` in Splunk
* Restart forwarder: `./splunk restart`

Search with:

```spl
index="splunkdemo2"
```
To edit, press i to insert, and to save  `:wq enter`.
  - Note: `9997` is the port to communicate through; we must let Splunk receive from `port 9997`.
  - Go to Splunk Homepage, `Settings`, click on `Forwarding/receiving`, `New receiving port`, type `9997`, and click on save.
  - Restart Splunk service on both servers, and to do that, we have to change the Directory `cd /opt/splunkforwarder/bin/` and `./splunk restart`

![image](https://github.com/user-attachments/assets/228d5da8-3e10-4910-addf-60af02f93c46)

![image](https://github.com/user-attachments/assets/7923cbfb-af06-4652-bc4b-06d30e0e0e50)

![image](https://github.com/user-attachments/assets/c1ad7c7d-f34d-412a-b663-e95759e1e1d1)

![image](https://github.com/user-attachments/assets/4144d5e9-1ca4-43fc-a305-d48906627d92)

![image](https://github.com/user-attachments/assets/d8a452ff-1f2d-4fc0-83ff-c20f772d4751)

![image](https://github.com/user-attachments/assets/8bf537ca-9eb4-40aa-a1fa-1fa5a03ab8bc)

![image](https://github.com/user-attachments/assets/c16124db-8252-4e33-a9f6-c55bccc02bf1)

### Step 4. Monitoring and Capturing SplunkForwarder Logs
- Go to your instance page and run the KyleTechForwarder instance
- Launch the KyleTech instance
- Log in to the Splunk Admin page and log in
- Go to Search, type `index="Splunkdemo2"`, enter 

![image](https://github.com/user-attachments/assets/7b4016c9-862b-432e-93b1-e423ae57c09d)

![image](https://github.com/user-attachments/assets/b4a82b92-80d7-4319-a02a-d81135768efa)

![image](https://github.com/user-attachments/assets/4e1642b4-79eb-47a8-8f3d-dfcf52a9f91e)

## Part 7: SPLUNK INTEGRATION WITH AWS
### Step 1. Log in to Splunk 
- Go to splunk.com and log in
- Click on Products
- Free trials and Downloads
- Universal Forwarder
- click Download under `64 Bit Windows 10, 11, Server, 2022`

### Step 2. Create an Instance in the AWS S3 Buckets
Note: Authentication (AWS Access key / Secret key) Splunk needs `AWS Authentication key` to access `AWS logs/data`, so we have to enable some services in `AWS`.
- - Create `S3 Buckets`
  - Go to AWS console and log in
  - Under search type S3
  - Click on S3 (Scalable storage in the cloud)
  - Click create Bucket
  - -  Fill out the Following:
    -  Name: `kylebucket7958`
    -  Object Ownership: Default (ACLs Disabled)
    -  Block Public Access: uncheck `block all access` and check `I Acknowledge ...`
    -  Note: Leave the remaining of the setting and under the Bucket key check `Disable` and Scroll down and click `Create Bucket`.
    
 ### Step 3. Create Access and Secret Keys in AWS
 - Click on the `account name` in the top right corner
 - Go to `Security and Credentials`
 - Scroll down to Access Key and click on `Create Access Key` NOTE: If you already have one, use that `Key ID` and `Secret KEY`, but if no,t proceed to this process
 - Check `other`, click on Next
 - Leave `Description tag` Click `Create Access Key`
 - Copy both Key ID and Secret Key and save them `in Notepad` because we will need them later.
 - Download the CSV File and save.
   

### Step 4. Log in to Splunk
- Create a new `index` to capture data in Splunk (Refer to `Part 6` `Step 2` and Name it :`AWScap`)
- Go to `Apps`, click on `Find More Apps`, Search `aws`, click on `Install Aws Add-on on Spluck` to install, Click `Open App`.
- Under Login and Install. Use your Splunk log in credentials to log in, `Username` and `Password` then click `Agree` and Install
- After installing click on `Open the App`.


### Step 5. Add Account with AWS Credentials. That's the (Access Key)
- Click on `Configuration`.
- Click on `Add` (Make sure you are in the `Account tab`)
- - Name: `AWSaccount`
  - Key ID : `AKIA4SZHNXLLHWZYK478`
  - Secret Key: `Sbs3XaNsWr++r99mn4tb159yTHHCRZbnYZ8EIDDc`
  - Region `Globa` and click `ADD`.

### Step 6. Create New Inputs
- Click on `Inputs`
- `Custom Data Type`
- Generic S3 and fill out the Forms
- - AWS Name: `S3dataonboarding`
  - AWS Account: 'AWSaccount`
  - Leave, `Assume Role/Region/Use Private Endpoint`
  - S3 Bucket: `klyebucket7958`
  - Leave `Key Prefix`
  - Start Date/Time: `2024 Back date the Date`
  - End Date/Time:
  - Source Type: AWS:`S3`
  - Index: `AWScap` and Click on `ADD` to Add

### Step 7. Upload Any CSV File an S3 Bucket
- Open the `S3 bucket` in a different Browser
- Locate your S3 name: `kylebucket7958` Click on the name
- Click `Upload`
- Click `add file`
- Locate our CSV file used from the beginning of this Lab, select Add, and click on `Upload`
- - Note: Now Splunk will go to AWS and ask for data from the S3 Bucket because we created an input around that Splunk will ask AWS to share that data with.
  - So AWS will request an authentication key before allowing Spluck to access the data.
  - Then Spluck will give the Authentication key, which was provided in the cost of creating the account
  - And then Spluck will log into AWS to fetch the requested data 


### 8. Verify if the inputs have been created
- Go to `Apps` in Splunk
- Click on `Search/reporting`
- - Type: `indes=awscap` press enter
  - Click on Host: You will see the `host IP` under Values
  - Click on Source: Under Value, you will see `S3://kylebucket7958/csvfile`
  - Click on Source Type: you will see `AWS: S3`



