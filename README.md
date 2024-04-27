y final test project from course Test Automation Selenium and Python

Commands for test runner
Use the following command to run all tests
pytest -v --tb=line --language=en .
Check test_login_page.py, test_main_page.py, test_product_page.py for page specific test run commands.
Used tools
Python 3.11
Selenium WebDriver
ChromeDriver
geckodriver
pytest
docker
 

How to run the tests on your machine
Create a local project using Virtualenv
 
Work tested for Chrome Version 110.0.5481.178 (Official Build) (64-bit)
Install GeckoDriver
Work tested for Firefox Version 110.0 (64-bit)
Add drivers to the Environment Variables based on your OS settings
[Windows] computerhope
Install requirements using the following command
pip install -r requirements.txt
Run the following command to start the tests
pytest -v --tb=line --language=en .
You can change webdriver to firefox
pytest -v --tb=line --language=en --browser_name=firefox .
You can change language to
['ru', 'en', 'fr', 'es']
Example:

pytest -v --tb=line --language=fr .
Use this sequence of commands to run the container:
To run the application in docker, you need to install docker-compose:
sudo apt install docker-compose 
Clone the repository
git clone https://github.com/Lexxx42/final_test_project.git
Change directory to project dir
cd final_test_project/
Create folder logs in clonned repository
mkdir logs
Start the build
docker-compose up --build
You can set ENTRYPOIN in docker-compose.yaml to start tests right away. Or use the commands with your docker image.
With volume if you need logs in a file. (Directory logs must be created before use of the command)

docker run -v ~/logs:/autotests/test_project/logs autotest_pytest pytest -v -s -rx -m negative --browser_name=firefox
And without volume.

docker run autotest_pytest pytest -v -s -rx -m negative
You are free to use all the test markings and/or files in this repository in a docker container.

Added feature to create html test reports
All reports saved to /logs directory

To use the feature use pytest commands without -s argument to capture the logs
pytest -m negative --tb=line
pytest -m negative --tb=line --browser_name=firefox
You can use those commands with docker container
docker run autotest_pytest pytest -m negative --tb=line
docker run autotest_pytest pytest -m negative --tb=line --browser_name=firefox
Reports will be saved to /logs directory so mount a volume You will need to create a directory logs in your current user's home directory

mkdir logs
docker run -v ~/logs:/autotests/test_project/logs autotest_pytest pytest -m negative --tb=line --browser_name=firefox
docker run -v ~/logs:/autotests/test_project/logs autotest_pytest pytest -m negative --tb=line
