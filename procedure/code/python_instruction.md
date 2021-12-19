# Python Insruction for installing PyPI and setting up Geckodriver broswer engine for reproducing Covid Academic analysis. 

Author: Emily Zhou   
Created: Fall 2021

## To run the python code provided by the original author, you need to have
    
    python 3 or above installed on you local computer
    
    firefox browser
  
  
## For mac OS Big Sur, Mojave, Catalina, High Sierra users: 

1. Launch Terminal by pressing command+space, type terminal and hit Enter key.

2. Download pip, a package management system used to install and manage software packages/libraries written in Python, using the command below directly. These files are stored in a large “on-line repository” termed as Python Package Index (PyPI).

     `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`

3. Now execute the downloaded file using below command

     `python3 get-pip.py`

4. Verify if the pip has been installed correctly by performing a version check on the same

     `pip3 --version`

5. Use the following commands to install the latest version of a module and its dependencies from the Python Package Index(PyPI). In this study, the original author has used the following three:

     `pip install python-dateutil

     pip install selenium

     pip install urllib3`

## Below are the steps essential to setup geckodriver!!!

6. Make sure to also install webdriver manager, otherwise the code would not work as we are pulling data from web. 

    pip install webdriver-manager

7. Install geckodriver on Mac. GeckoDriver is a web browser engine which is used in many applications developed by Mozilla Foundation and the Mozilla Corporation. GeckoDriver is the link between the tests in Selenium and the Firefox browser. There are engines that allows you pull data from websites.As it seems that the original authors have used the firfox broswer, to fully reproduce the study, let's stick with geckodriver here.These two commands might take a while to run: 

     `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null

     brew install geckodriver`

8. Three lines of code from the original analysis needs to be corrected, simply because geckodriver executable needs to be in PATH

     `from webdriver_manager.firefox import GeckoDriverManager
     
     from selenium.webdriver.firefox.service import Service
    
     gecko = webdriver.Firefox(service=Service(GeckoDriverManager().install()))`


9. Finally, you might run into the error of python reporting: "Unable To Get Local Issuer Certificate In Mac OS". If so,

    `Open mac os finder, then click Applications —> Python 3 folder to expand it.
    
    Double click the Install Certificates command file to run it. It will open another popup terminal window and show command execution output text.
    
    Close the popup window when the command runs completely successfully. Now run the python code again, the Certificate Verify Failed Error will disappear.`
  
10. Now we are able to run the code. If using python IDLE, simply hit "RUN", if using terminal:

   `python3 filename.py`


## Helpful resources:

https://www.geeksforgeeks.org/how-to-install-pip-in-macos/
https://docs.python.org/3/installing/index.html
https://stackoverflow.com/questions/40208051/selenium-using-python-geckodriver-executable-needs-to-be-in-path
https://www.dev2qa.com/how-to-fix-python-error-certificate-verify-failed-unable-to-get-local-issuer-certificate-in-mac-os/
https://stackoverflow.com/questions/64717302/deprecationwarning-executable-path-has-been-deprecated-selenium-python
https://api.biorxiv.org/covid19/help
OR: https://api.biorxiv.org/details/medrxiv/help