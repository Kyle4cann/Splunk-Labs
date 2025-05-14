# Securing-Infrastructure-LAB
### NAME: VINCENT CANN.
### STUDENT ID: 4381913
### COURSE: CYBS 1007 SECURING INFRASTRUCTURE.


## Lab 1 Part 1: Create AWS account. 

### Step 1. 
- open https://aws.amazon.com/console/ in your browser
- click on account and AWS management console
- click on Create a new AWS Account
- Fill in: Root user email address and AWS account name the click of verify email address
- Open your mail to verify account
### Step 2.
- open https://aws.amazon.com/console/ in your browser
- click on account AWS management console
- Click on Sign in using root user email
- Enter Email, the characters given to you click on i'm not a roboot to enter password to login
### Step 3:
- At the search buttom type ES2 and click on Instances
- Click on Launch an instance
- Enter Fill out or configure your server
- ### Notes:
- - Enter Name
  - Select Ubuntu under Application and OS Image: Slpunk is very compartible with ubuntu because it liter
  - For splunk to run smoothly its requires minimum of 2gig Virture CPU and 4gb Memory So select T3 meduim
  - Click Key Pair to create Key Pair (SplunkTest )
  - Under security Group select Allow All.
  - Change storage to 30gb Because you eligible to use up to 30gb
- Now click on Launch instance to create  Instance Called (KyleTech)
### Step 4:
- Check Instance Box and click on connect
- ### Note:
  Its will locate you to a terminal page.

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

## Part 2 Installing Splunk on Ubuntu Server Created on AWS

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
- - Sudo su ( To root user)
  - cd /opt ( To the Directory of Splunk installation)
  - Copy and Paste the link
  - ls ( To View file downloader to the Director)
  - dpkg -i splunk-9.4.2-e9664af3d956-linux-amd64.deb (To extract files to splunt default folder)
  - sudo su splunk (to move root to splunk directory)
  - cd splunk/bin
  - ./splunk start --accept-license --answer-yes
  - Enter Username
  - Enter Password
  - We will get our IP: as http://172.31.21.104:8000
    
 ### Step 3. Allowing Port
 - Go to AWS under Instance created and copy the Public ip address paste in your url as shown: 3.17.109.107:8000 
  - #### Note:
    Its will not connect because in setting up our instance, we only allowed 3 ports and splunk runs on port number: 8000
- Click on Instance Name
- Security, Security Group, Open link in new tab, Edith Inbond Rules Add Rules, Custom IP 8000, and allowing forward enter 0.0.0.0/0 , Change Custom TCT to All Trafic for study purpose
- Click Save Rules
- Now we go back to refresh our splunk login page:

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



## Part 3: Creating user in Splunk
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
- Select toolsfairy and Download CSV file
### Step 2 Add Downloaded CSV File (Select Source)
- Login to Splunk Home Page
- Click on Add data
- Click on Upload
- Select File Sample-CSV-file
- Click Open to load file
- ### Note: Under Set Source Type
- If Timestamp is not showing Enable by:
- - Click on Timestamp
  - Select  Current and Save
- ### Under Input Settings
- Click on Create a new index
- Name it Splunkdemo and Save
- Select Splunkdemo
- Review and Submit
### Step 3. Searching
- Click on Start Searching
- In New Search type index="Splunkdemo" to load Static File
- Select All time set time to prefferred time frame and press enter to search
- 

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

### Part 5. Splunk Processing Language.
SPL: Splunk Processing Language is used to search and retrieve stored data (Playing arround Fields and creating Visualization)
### Step 1. Adding to Index
- Under Search type index= index name eg index="_internal"
- Add Host IP
- Add Source (Matrix)
- Add Source Type (Splunkd)
### Step 2. Modify timestamp
This enhances searching 
- Earliest Field (earliest= -15m@m), this means that i want to search data for the first 15 minutes
- Latest Field (latest= -1m@m) Mean search data for last minute
### Step 3. Graphs
- Stats convert to Table
- Chart Convert to Graph on X and Y Axis
- Time Chart convert to graph on Time Note: before transforming, you will need PY (|) followed by command eg, index="_internal" | Stats Count by group., | Chart count by name., | Time Chart by Series
### Step 4. Creating Dashboard
- Click Edit from the homepage
- Add Panel
- Select preferred Chart
- Copy and paste the Search History and click Add Dashboard

![image](https://github.com/user-attachments/assets/07ea85df-4398-44cf-9281-e7d2f9226073)

![image](https://github.com/user-attachments/assets/1d5b0e8b-018d-4022-baac-6acf1fa98dc2)

![image](https://github.com/user-attachments/assets/067bdc29-c082-4e17-8abc-1fdc50e7f656)

![image](https://github.com/user-attachments/assets/d6e26efc-92d4-4ee3-bd19-9c4d41a14090)

![image](https://github.com/user-attachments/assets/357b5497-0c38-4553-a8ff-4646503ee3c7)

![image](https://github.com/user-attachments/assets/b01644f5-488f-4eed-9fae-fc63bcd7343a)

![image](https://github.com/user-attachments/assets/c7da3c3f-476a-4719-b60b-31fd701b9d6f)

![image](https://github.com/user-attachments/assets/a6771375-29c9-4758-bddd-b1d0c5923f5c)

![image](https://github.com/user-attachments/assets/ae8c94cf-3b0e-4a5a-906d-96f9aef70cb9)




