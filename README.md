# How to create a Django Application

Django consist of one main project that can contain multiple projects.

## Start the first App

1. Create a python virtual environment:

        python3 -m venv "Folder Name"

2. Run your python venv:

       source "Folder Name"/bin/activate

3. Install Django in the Virtual environment:

        pip install django

## Django First Project

First with need to create our firstproject
>Projects can have multiple applications

        django-admin startproject "Project Name" "PATH"

After creating the project will be using manage.py to create the projects app. For information of folder and structure of the project visit:https://docs.djangoproject.com/en/3.2/topics/


## Create the First App that will handle page rendering

1. Run

        python manage.py startapp "App Name"

2. Register the new app in the settings.py inside your project folder "project folder"/settings.py

        INSTALLED_APPS = [
        ++ 'pages.apps."your app config name',
            'django.contrib.admin',
            'django.contrib.auth',
            'django.contrib.contenttypes',
            'django.contrib.sessions',
            'django.contrib.messages',
            'django.contrib.staticfiles',
            ]

3. Create a urls.py in your app folder 
    - import path from django

            from django.urls import path

    - Import the views methods that the urls will use 

            from . import views
    - Define the path for the url:

            urlpatterns= [
                path('',views.index, name='index')
                ]
    
    - Final Code
    
            from django.urls import path
            from . import views

            urlpatterns= [
                path('',views.index, name='index')
                ]

5. Define your method in the views file:

        from django.shortcuts import render
        from django.http import HttpResponse
        def index(request):
            return HttpResponse('<h1>Hello World</h1>')

6. Register the app url in the project url:


        from django.urls import path,include

            urlpatterns = [
           ++ path('', include('pages.urls')),
            path('admin/', admin.site.urls),
            ]


## Create a Template folder

Create the template folder inside the app an add the html file with the jinja syntax


## Add Static Folder to our projects

Inside the project folder create a static folder and then add the configuration to the settings

        STATIC_ROOT = os.path.join(BASE_DIR, 'static')
        STATIC_URL = '/static/'
        STATICFILES_DIRS = [
                os.path.join(BASE_DIR, 'btre/static')
                ]


    