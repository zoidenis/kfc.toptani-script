Description

kds.toptani-scripts is a collection of scripts developed specifically to automate processes in Chrome and integrate work with GitHub for KFC Toptani. This documentation includes steps for installing Python, setting up ChromeDriver, running automation scripts, and configuring GitHub for cloning and updating the local repository.

Requirements

	•	Python 3.8+ for script execution.
	•	Chrome and ChromeDriver for browser-based automation.
	•	Git for version control and syncing with GitHub.

Installation Steps

1. Download and Install Python for Windows

	1.	Visit the official Python website and download the latest version of Python for Windows.
	2.	During installation, make sure to check the Add Python to PATH option.
	3.	After installation, verify by opening cmd and typing: 
      python --version
   	  # This should display the installed Python version.

2. Install ChromeDriver

	1.	Find the version of Chrome you have installed by going to Settings > About Chrome in your browser.
	2.	Download the ChromeDriver that matches your version from the ChromeDriver download page.
	3.	Extract ChromeDriver and place chromedriver.exe in a folder included in PATH or in the same folder as the scripts.

3. Install Project Requirements

	1.	After cloning the repository from GitHub (see GitHub setup steps below), install the project requirements using requirements.txt:
      pip install -r requirements.txt

Running the Chrome Automation Script

	1.	Open an editor like Visual Studio Code or a terminal, then navigate to the folder where the script is located.
	2.	Run the automation script for Chrome. Here’s an example script that uses Selenium to open Chrome:
 	3.	Make sure path/to/chromedriver.exe matches the location of your chromedriver.exe.

GitHub Setup and Sync with KDS

1. Configure Git for Local Repository

If not configured previously, set up your Git username and email:
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"

2. Clone the Repository from GitHub

	1.	Clone the kds.toptani-scripts repository to your local computer: 
      git clone https://github.com/[username]/kds.toptani-scripts.git

	2.	Navigate into the cloned directory:
      cd kds.toptani-scripts

3. Using Git to Fetch Updates from the Repository

Once you’ve made changes in your local repository, you can commit and push updates to GitHub:
   git add .
   git commit -m "Updates to Chrome automation"
   git push origin main

To fetch the latest updates from GitHub into your local repository:
   git pull origin main

Automating with a .bat Script

To automate the process of pulling updates from GitHub and running the Python script, you can use the following .bat script:
   @echo off
   REM Navigate to the folder where the repository is cloned
   cd C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts\kfc-scripts

   REM Pull the latest version from GitHub
   git pull origin main

   REM Run the Python script
   python kds.toptani-bucket.py

   REM Keep the window open to view results
   pause

Instructions for the .bat Script:

	1.	Save the code above in a file named run_kds_script.bat.
	2.	Adjust the path (cd C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts\kfc-scripts) on line 2 to match the location of your repository.
	3.	Run run_kds_script.bat to automatically pull updates and execute the Python script.
