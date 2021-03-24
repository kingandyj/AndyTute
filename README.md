# django-container-base
Docker container hosting a base Django App

# Installation

From your container folder `./`, the following files and structure should be present at minimum:
    
``` 
./
├── Dockerfile
├── README.md
├── djangocontainerbase/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── docker-compose.yml
├── .env
├── .env.example
├── manage.py
└── requirements.txt
```

1. `cp .env.example .env`
2. Edit `.env` in a text editor to change secret variables
3. `docker-compose up --build`
4. Browse to http://localhost:$APP_PORT (as specified in `.env`)
5. Cheer that the project is successfully working, and close it using `$ docker-compose down` before proceeding with additional initial configuration described below.

# Change the project name to *\<newprojectname\>* before beginning any development [^1]

1. Change project folder name 

    `$ mv ./djangocontainerbase ./<newprojectname>`

2. Change  in **./*\<newprojectname\>*/settings.py** to *\<newprojectname\>*

    a. `""" Django settings for <newprojectname> project.`
    
    b. `ROOT_URLCONF = '<newprojectname>.urls'`
    
    c. `WSGI_APPLICATION = '<newprojectname>.wsgi.application'`

3. Change djangocontainerbase in **./*\<newprojectname\>*/urls.py** to *\<newprojectname\>*

    a. `"""<newprojectname> URL CONFIGURATION`

4. Change djangocontainerbase in **./*\<newprojectname\>*/wsgi.py** to *\<newprojectname\>*

    a. `""" WSGI config for <newprojectname> project.`
    
    b. `os.environ.setdefault("DJANGO_SETTINGS_MODILE", "<newprojectname>.settings")`

5. Change djangocontainerbase in **./manage.py** to *\<newprojectname\>*

    `os.environ.setdefault("DJANGO_SETTINGS_MODULE", "<newprojectname>.settings")`

6. If other files exist in the **./\<newprojectname\>/** folder other than those listed above, ensure that all references to djangocontainerbase are changed to *\<newprojectname\>* as demonstrated above.

7. Save and rebuild container

    `$ docker-compose up`
    
[^1]: Instruction set source: https://youtu.be/ko83PEvotNI
