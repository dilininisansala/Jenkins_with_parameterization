# How to run automation tests in Jenkins with parameterization
# Step 1: Set Up Jenkins
Start by installing it and setting up a Jenkins server
Open Jenkins in your browser (http://localhost:8080) and log in

# Step 2: Create a New Jenkins Job
In Jenkins, go to Dashboard > Click on + New Item
Enter an item name for your job and select Pipeline or Freestyle project depending on your preference
Click OK to create the job
![2](https://github.com/user-attachments/assets/9f4ba458-a1f4-4180-ada9-7b993c39c79a)

# Step 3: Enable Parameterization in Your Job
In your new job configuration page, scroll down
Check the 'This project is parameterized' option
Click on Add Parameter and choose the type of parameter you need
Common parameter types include:
* String Parameter: For passing text values.
* Choice Parameter: For selecting from a list of options.
* Boolean Parameter: For a simple true/false option.

Enter details for each parameter, such as name, default value, and description. These parameters will be passed to your test automation script.
![8](https://github.com/user-attachments/assets/19b8aeea-1426-44b3-8396-a544cbf0a720)

# Step 4: Configure Your Automation Script to Accept Parameters
Your test scripts should be able to receive parameters from Jenkins. If you're using Python, you can pass arguments through the command line and access them within your script

# Step 5: Set Up Your Jenkins Job to Run the Script with Parameters
Scroll down to the 'Build Steps' section
Select 'Execute Windows batch command (for Windows)' or 'Execute shell (for Linux)'
Use the parameters in your command
Here, use the %WORKSPACE% Variable to reference the workspace directory where Jenkins checks out your project files
![14](https://github.com/user-attachments/assets/625228b5-3c51-4953-b904-348579cd5f51)

For example:
cd %WORKSPACE%
pytest --browser %Browser% --url %URL% --html=report.html

Then click on Apply and Save 

# Step 6: Run the Jenkins Job with Parameters
Go to the job's main page in Jenkins
Click on 'Build with Parameters' on the left menu
Choose your parameters (Eg: Browser, URL) and click on Build
![11](https://github.com/user-attachments/assets/62ac8704-4843-4fdf-809e-140916c5a5b9)
![5](https://github.com/user-attachments/assets/4ea54aa8-ef13-49e0-aecd-13484a64e5f3)

# Step 7: Review the Console Output
Once the job starts, click Console Output to view the progress. 
The console output should display the selected parameters and any logs from your automation test
![12](https://github.com/user-attachments/assets/db36eeea-8978-400e-aad7-ca55352f611d)

The Test Report
![16](https://github.com/user-attachments/assets/7422ce0d-c62f-4d2c-900c-5a6b58db2d61)

# Additional Tips
Test Reporting: You can use plugins like JUnit or Allure for reporting test results in Jenkins.

With these setups, you now have an automated and parameterized Jenkins job for running tests across different environments and configurations.

