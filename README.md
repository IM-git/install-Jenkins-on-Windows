Introduction
--
___
Manual for install Jenkins and addition stuff(used Windows 10). Solving the errors I had to face.
___

**Step 1:**
* Open "https://www.jenkins.io/download"
* Select on the left side version for your system. In my case this is Windows  
* Download it. **(Don't install yet)**

**Step 2:**
* In the second step is open "https://www.oracle.com/java/technologies/downloads/#java11" 
  >+ You must create/use your account there 
  >+ For Jenkins need install JDK 11(Jenkins project performs a full test flow with the following: OpenJDK JDK / JRE 8 - 64 bits; OpenJDK JDK / JRE 8 - 64 bits) https://www.jenkins.io/doc/administration/requirements/java/  
* Download it and install 

**Step 3:**
* Right-click "Start button"
* Click "Windows PowerShell"
* Perform command: java -version. The answer should be: *java version "11.0.14"*.

  (Or another way: Click "Win + R" => Enter a value: "cmd" => On the command prompt perform: java -version)


***If another answer:***

*Step 3.1:*
* Click "Start button" 
* Enter "edit the system environment variables" in the search bar and open it
* In the bottom right corner click on "environment variables" button 
* Where "system variable", find and click "Path" line 
* Click "Edit" 
* If there exist for example: *"C:\Program Files\Java\jdk-17.0.2"* this needs to be replaced with  that we installed: *"C:\Program Files\Java\jdk-11.0.14"* 
* If there exists a line with *"C:\Program Files\Common Files\Oracle\Java\javapath"*, need to delete this path 
* Click "Ok"

*Step 3.2:*
* Where "system variable", find and click "JAVA_HOME" and change the path to  *"C:\Program Files\Java\jdk-11.0.14"* 
  + If this path not exist, create "JAVA_HOME" with the path *"C:\Program Files\Java\jdk-11.0.14"*

*Step 3.3:*
* Repeat "Step 3". Now  should be displayed version is *"11.0.14"*

**Step 4:**

Install Jenkins and select logon type run service as local or domain user.  When we have error there, we have to create new user: 

* Click "Start button" 
* Enter "Add edit or remove other users" in the search bar and open it 
* Click "Add someone else to this PC" 
* Opens "How will this person sign in?", Click on "I don't have this person's sign-in information" 
* Click on "Add a user without a Microsoft account" 
* Come up your own username and password and Click "Next".

**Step 5:**
* Click "Start button" 
* Enter "Local Security Policy" in the search bar and open it 
* Click on "Local Policies" 
* Click on "User Rights Assignment" 
* By the right side showing the "Policy" need find and double click "Log on as a service" 
* Click on "Add Users or Groups" button 
* Enter the object name, which we created in the previous step 
* Click on "Check Name" to verify 
* Click "Ok".

**Step 6:**

Install the Jenkins that was downloaded in the first step:

* Click "Next" 
* "Destination folder"  by default just click "Next" 
* Select "Run service as local or domain user". Account and password is your username and password which was created on the previous steps. Click "Next" 
* Click "Test port", click "Next" 
* Click "Change", specify the path with version which installed(*C:\Program Files\Java\jdk-11.0.14*) , click "Ok", click "Next" 
* In the "Custom Setup" need to select in "Start Service" and "Firewall Exception" the parameter "Entire feature will be unavailable ", after that click "Next" 
* Click "Install"

**Step 7:**
* Click "Start button" 
* Enter "Services" in the search bar and open it 
* Find "Jenkins" in the list, right-click on it 
* Select "Start"
  
*Step 7.1:*

***If an error appears 1069  "the service did not start due to a logon failure":***
* Right-click on "Jenkins" 
* Select "Properties" 
* Select the tab "Log on" 
* Select "Local System account" 
* Click "Apply" 
* Click "Ok" 
* Right-click on "Jenkins" 
* Select "Start" 
* After that click "Stop" 
* Right-click on "Jenkins" 
* Select "Properties" 
* Select the tab "Log on" 
* Select "This account" 
* Enter the same username and password which use when was installing Jenkins 
* Click "Apply" 
* Click "Ok" 
* Right-click on "Jenkins" 
* Select "Start"

**Step 8:**
* Open browser 
* Enter "http://localhost:8080/" in the address bar, (Port 8080 by default, if you changed port when installed Jenkins use yours) 
* In the opened page shown path to password, copy password from there and use it for "Administrator password", click "Continue" 
* Click "Install suggested plugins" (need to wait some time for the installation) 
* Come up username, password and ect, click "Save and Continue" 
* Click "Save and Finish" 
* Click "Start using Jenkins". (in the next time for login use it username and password).

**Step 9:**
* When you not use Jenkins, it can be stopped. Click "Start button" 
* Enter in the search bar "Services" and open it 
* Find "Jenkins" in the list, right-click on it 
* Select "Stop". To run Jenkins  the same actions and select "Start".


***Sources I used to solve problems:***

https://www.youtube.com/watch?v=XuMrEDA8cAI&ab_channel=CloudBeesTV    
https://www.youtube.com/watch?v=byjXxdAQeRM&ab_channel=KapilAryaMicrosoftMVP    
https://youtu.be/1y8RsUbxtAw    
https://stackoverflow.com/a/68926826    
https://stackoverflow.com/a/70044365    
https://www.jenkins.io/doc/book/installing/windows/ 