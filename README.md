# django-elastic-apm-docker
Very simple steps to enable elastic amp to collect informations from your django application. everything in dockers :)


Steps:

1. Download the two yml files and keep them in the same directory!
2. Make sure you have docker-compose
3. run the below command,

# docker-compose up -d

give it a few mins!

Now add the following to you django applications settings.py

ELASTIC_APM = {
  'SERVICE_NAME': 'Your service name',
  'SERVER_URL': 'http://localhost:8200',
}

now install elasticapm for django through pip

pip install elastic-apm
pip install psutil

and add it to INSTALLED_APPS.

'elasticapm.contrib.django'

now add the elasticapm middleware to the MIDDLEWARE.

'elasticapm.contrib.django.middleware.TracingMiddleware',

save the settings and makemigrations & migrate the project.

Now start the project,

Under the project terminal, you can test the connectivity by,

# ./manage.py elasticapm check
# ./manage.py elasticapm test

You will see results like,

Trying to send a test error to APM Server using these settings:

SERVICE_NAME:   your service name
SECRET_TOKEN:   None
SERVER:         http://localhost:8200

Success! We tracked the error successfully! You should be able to see it in a few seconds at the above URL

Now login to kibana and load apm.

Tadaaa!
