Automating Google Chrome in Kiosk Mode Using Selenium

This guide demonstrates how to automate the opening of Google Chrome, log into a website, and open it in kiosk mode using Selenium in Python.

Requirements: 

1. Python installed on your system. 
Link: https://www.python.org/downloads/release/python-3130/

2. Selenium installed (use `pip install selenium`). 
Open CMD Run as Administrator
Type “cd C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts”
Type “Pip install selenium”

3. Download the ChromeDriver matching your version of Chrome.
Link: https://storage.googleapis.com/chrome-for-testing-public/130.0.6723.69/win64/chromedriver-win64.zip
Extract to “C:\ChromeDriver\chromedriver-win64\chromedriver.exe”

4. Git Installation on your system.
Link: https://github.com/git-for-windows/git/releases/latest
Open CMD Run as Administrator
Type “cd C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts”
Type “git clone https://github.com/zoidenis/kfc.toptani-script.git”

Python Script: 

Here is the Python script that automates the process of opening Google Chrome, logging in, and enabling Kiosk Mode:

from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time


# Vendosni shtegun e ChromeDriver
driver_path = r'C:\ChromeDriver\chromedriver-win64\chromedriver.exe'


# Krijoni opsione për Chrome
chrome_options = Options()
# Mbyllni shfletuesin vetëm manualisht
chrome_options.add_experimental_option("detach", True) 
# Enable kiosk mode
chrome_options.add_argument('--kiosk')


# Krijoni një instancë të ChromeDriver
service = Service(driver_path)
driver = webdriver.Chrome(service=service, options=chrome_options)


# Zëvendësoni me URL-në e faqes suaj të logimit
driver.get("https://kfcal-live.iprojectdev.com/admin/") 


# Pritni disa sekonda për ngarkimin e faqes
time.sleep(3) 


# Pritni derisa fusha e emrit të përdoruesit të jetë e dukshme
username_field = WebDriverWait(driver, 10).until(
   EC.presence_of_element_located((By.XPATH, "//input[@name='log[user]']"))
)


# Dërgoni emrin e përdoruesit me JavaScript
# Zëvendësoni me emrin tuaj të përdoruesit
driver.execute_script("arguments[0].value = 'kds.toptani';", username_field) 


# Pritni derisa fusha e fjalëkalimit të jetë e dukshme
password_field = WebDriverWait(driver, 10).until(
   EC.presence_of_element_located((By.XPATH, "//input[@name='log[pass]']"))
)


# Dërgoni fjalëkalimin me JavaScript
# Zëvendësoni me fjalëkalimin tuaj
driver.execute_script("arguments[0].value = '1234';", password_field) 


# Gjeni butonin e dërgimit dhe klikoni
submit_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[12]/form/table/tbody/tr[4]/td/div"))
)
# Klikoni butonin e dërgimit
submit_button.click() 
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Replace with the desired URL after login
target_url = "https://kfcal-live.iprojectdev.com/admin/#/Orders_monitor/1"
driver.get(target_url)
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
fullscreen_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[1]/div[3]/ul/li/a/i"))
)


# Klikoni butonin e dërgimit
fullscreen_button.click() 
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
switch_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[3]/div[2]/div[1]/div[5]/div[4]"))
)


# Klikoni butonin e dërgimit
switch_button.click()
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
tiles_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[3]/div[2]/div[1]/div[5]/div[5]/div[3]/label"))
)


# Klikoni butonin e dërgimit
tiles_button.click()
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
switch_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[3]/div[2]/div[1]/div[5]/div[4]"))
)


# Klikoni butonin e dërgimit
switch_button.click()
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
dropstore_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[3]/div[2]/div[1]/div[2]"))
)


# Klikoni butonin e dërgimit
dropstore_button.click()
# Pritni disa sekonda për të parë rezultatin pas logimit 
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
options = WebDriverWait(driver, 10).until(
   EC.presence_of_all_elements_located((By.XPATH, "//ul[contains(@class, 'select2-results')]//li"))
)


# Zgjidhni opsionin e dëshiruar
for option in options:
   if "44088702 - KFC Toptani" in option.text:
       option.click()
       break
   # Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
dropmonitor_button = WebDriverWait(driver, 15).until(
   EC.element_to_be_clickable((By.XPATH, "//html/body/div[3]/div/div/div/div[6]/div[1]/div[3]/div[2]/div[1]/div[3]/div"))
)


# Klikoni butonin e dërgimit
dropmonitor_button.click() 
# Pritni disa sekonda për të parë rezultatin pas logimit
time.sleep(5)


# Gjeni butonin e dërgimit dhe klikoni
options = WebDriverWait(driver, 10).until(
   EC.presence_of_all_elements_located((By.XPATH, "//ul[contains(@class, 'select2-results')]//li"))
)


# Zgjidhni opsionin e dëshiruar
for option in options:
   if "Drinks" in option.text:
       option.click()
       break


.Bat Script:


Use git pull to fetch the latest version from GitHub, then run the Python script with python script_name.py. Put it on the windows startup tu run every start of pc.

@echo off
REM Navigo në folderin ku ke klonuar depozitën
cd C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts\kfc-scripts


REM Tërheq versionin më të fundit nga GitHub
git pull origin main


REM Ekzekuto skriptin Python
python kds.toptani-bucket.py


REM Mbaj dritaren të hapur për të parë rezultatet
pause




