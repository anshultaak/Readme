
### What is Synthetic Monitoring?

Synthetic or directed monitoring is a method to monitor your applications by simulating users – directing the path taken through the application. This directed monitoring provides information as to the uptime and performance of your critical business transactions, and most common paths in the application. The simple reality is that there is no easy way to combine the accessibility, coherence, and manageability offered by a centralized system with the sharing, growth, cost, and autonomy advantages of a distributed system. It is here, at this intersection, that businesses turn to IT development and operations teams for guidance—APM tools enable them to negotiate these gaps.


### When deploying the application with Azure Pipeline, The most likely error are occur as follows:






### we can run the script in the local machine with these following steps:

```Step 1: ``` Installing Google Chrome

```
wget -nc https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb 
```

```
sudo apt update 
sudo apt install -f ./google-chrome-stable_current_amd64.deb 
```

```Step 2: ``` Installing Python

```
sudo apt install python3
```

```Step 3: ``` Installing Selenium and Webdriver for Python

 a. Create a directory to store Python scripts. Then switch to the newly-created directory

 ```
 mkdir tests && cd tests 
 ```

 b. Set up the Python virtual environment and activate it.

 ```
 python3 -m venv venv 
 source venv/bin/activate 
 ```

 c. Now use PIP to install the selenium and webdriver-manager Python modules under the virtual environment.

 ```
  pip install selenium webdriver-manager 
```

 d. Create a Python script and edit it in your favorite text editor:

 ```
 nano Synthetic.py
 ```

 e. Example the following Selenium Python script to the file:

 ```
 import time
 from selenium import webdriver
 from selenium.webdriver.common.by import By
 from selenium.webdriver.common.keys import keys
 
 username = ""
 password = ""
 driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)
 
 driver.get("https://python.org")
 time.sleep(5)
 driver.close()
 ```
f. Now, run this Python script in a shell.
```
python3 Synthetic.py
```



### For troubleshooting the error

```STEP 1: ``` When we run the script on our local machine, the "Page Not Found" error often occurs.



```STEP 2: ``` When we run the script and, in case we face some error, we can check the error with developer tools.

  a. By clicking the right side of three browsers, you can access the developer tools:

  <img width="202" alt="image" src="https://user-images.githubusercontent.com/76546821/215445810-67f3887e-5e89-4881-b50c-cfd582825379.png">

  b. Under the Developer Tools settings, you need to select the Network option where you are able to see the actual URL it is failing on.

  <img width="416" alt="image" src="https://user-images.githubusercontent.com/76546821/215447621-eeb26b73-76f9-4ef8-ad47-edcbe4fb6884.png">


```STEP 3: ``` We can log in to Azure and go to the server to check the health of the application. There, we can check if the application is running properly or not.

```Step 4: ``` For further investigation, we can log in to Grafana and check the dashboard and panel. Under the panel, we can see if the database connection is stable, and we can also view memory and CPU utilization.

  a. With this URL, you can log in to Grafana.
  
  ```
  url
  ```

```STEP 5: ``` If we are still getting errors in the application, we have only one way to resolve this issue: we need to check with the developer.

