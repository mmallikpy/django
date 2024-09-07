# Django
# Web development practice
1. <a href="#section1">How to install virtual environment in windows PC for django project.</a>
2. <a href="#section2">How to create a project</a>
3. <a href="#section3">How to create a app</a>
4. <a href="#section4">How to add app in setting.py</a>
5. <a href="#section5">How to run server</a>
6. <a href="#section6">How to create database{Model}</a>
7. <a href="#section7">How to create view</a>
8. <a href="#section8">How to create template</a>
9. <a href="#section9">How to extend a page</a>
10. <a href="#section10">How to migratations a database</a>
11. <a href="#section11">How tp migrate</a>
12. <a href="#section12">How to insert data in database</a>
13. <a href="#section13">How to view data from database</a>
14. <a href="#section14">How to edit data</a>
15. <a href="#section15">How to delete data</a>

<hr>
<h3>1</h3>
<span id="section1">
  - Install the python     &emsp;&emsp;&emsp;&emsp; [ https://www.python.org/downloads/ ] <br>
  - Install the pip        &emsp;&emsp;&emsp; &emsp;&emsp; [ If not available in your PC ]<br>
  - pip install pipenv<br>
  - Create a folder in your computer HDD and open a terminal at that direcoty<br>
  - pipenv shell<br>
  - Expected output       &emsp;&emsp;&emsp;&emsp; [ (Practice-fViqD9Aw) G:> ]<br>
  - pipenv install django<br>
</span>
<h3>2</h3>
<span id="section2">
  - > python manage.py startproject PROJECT_NAME
<span">

<h3>3</h3>
<span id="section3">
  - >cd PROJECT_NAME         &emsp;&emsp;&emsp;&emsp; [ You cannot locate the manage.py file if you do not open the project folder. ] <br>
  - >python manage.py startapp APP_NAME
<span">

<h3>4</h3>
<span id="section4">
  - >Open the setting.py file in your project folder. The INSTALLED_APPS = [] section will be there. Add the name of your app there.<br>
  - Example:
  
  INSTALLED_APPS = [ <br>
    &emsp;"django.contrib.admin",<br>
    &emsp;"django.contrib.auth",<br>
    &emsp;"django.contrib.contenttypes",<br>
    &emsp;"django.contrib.sessions",<br>
    &emsp;"django.contrib.messages",<br>
    &emsp;"django.contrib.staticfiles",<br>
    &emsp;"APP_NAME",<br>
]
<span>

<h3>5</h3>

<span id="section5">
  - > python manage.py runserver

  Output:<br>
  &emsp;&emsp; Starting development server at http://127.0.0.1:8000/<br>
  - visit this url.<br>
<span>

<h3>6</h3>
<span id="section6">
  - Open the models.py file from your project folder.<br>
  Example:<br><br><br>
  from django.db import models <br><br><br>
  class device(models.Model):<br>
    &emsp;&emsp;device_name = models.CharField(max_length=100)<br>
    &emsp;&emsp;device_ip = models.CharField(max_length=100)<br>
    &emsp;&emsp;device_brand = models.CharField(max_length=100)<br>
    &emsp;&emsp;device_type = models.CharField(max_length=100)<br>
    &emsp;&emsp;device_users = models.IntegerField()<br>
  
<span>
