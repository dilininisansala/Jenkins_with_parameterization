# How to run automation tests in Jenkins with parameterization
# Step 1: Set Up Jenkins
Start by installing it and setting up a Jenkins server
Open Jenkins in your browser (http://localhost:8080) and log in

# Step 2: Create a New Jenkins Job
In Jenkins, go to Dashboard > Click on + New Item
Enter an item name for your job and select Pipeline or Freestyle project depending on your preference
Click OK to create the job

# Step 3: Enable Parameterization in Your Job
In your new job configuration page, scroll down
Check the 'This project is parameterized' option
Click on Add Parameter and choose the type of parameter you need
Common parameter types include:
* String Parameter: For passing text values.
* Choice Parameter: For selecting from a list of options.
* Boolean Parameter: For a simple true/false option.

Enter details for each parameter, such as name, default value, and description. These parameters will be passed to your test automation script.

# Step 4: Configure Your Automation Script to Accept Parameters
Your test scripts should be able to receive parameters from Jenkins. If you're using Python, you can pass arguments through the command line and access them within your script

# Step 5: Set Up Your Jenkins Job to Run the Script with Parameters
Scroll down to the 'Build Steps' section
Select 'Execute Windows batch command (for Windows)' or 'Execute shell (for Linux)'
Use the parameters in your command
Here, use the %WORKSPACE% Variable to reference the workspace directory where Jenkins checks out your project files

For example:
# cd %WORKSPACE%
# pytest --browser %Browser% --url %URL% --html=report.html

Then click on Apply and Save 

# Step 6: Run the Jenkins Job with Parameters
Go to the job's main page in Jenkins
Click on 'Build with Parameters' on the left menu
Choose your parameters (Eg: Browser, URL) and click on Build

# Step 7: Review the Console Output
Once the job starts, click Console Output to view the progress. 
The console output should display the selected parameters and any logs from your automation test

# Additional Tips
Test Reporting: Use plugins like JUnit or Allure for reporting test results in Jenkins.

With these setups, you now have an automated and parameterized Jenkins job for running tests across different environments and configurations.

