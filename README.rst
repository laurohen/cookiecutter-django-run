project_django
==============

Behold My Awesome Project!

.. image:: https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg
     :target: https://github.com/pydanny/cookiecutter-django/
     :alt: Built with Cookiecutter Django
.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
     :target: https://github.com/ambv/black
     :alt: Black code style


:License: MIT

Changes to run this project quickly:
--------

* Create an .env file at the root of the project with value:

::

    DATABASE_URL=127.0.0.1
    USE_DOCKER=yes
    POSTGRES_HOST=postgres
    POSTGRES_PORT=5432
    POSTGRES_DB=bd_django
    POSTGRES_USER=postgres
    POSTGRES_PASSWORD=12312300
    
* Need to change default value in the file within the project /config/settings/base.py

    READ_DOT_ENV_FILE = env.bool("DJANGO_READ_DOT_ENV_FILE", True)


* Setting Up Development Environment
* Make sure to have the following on your host:

::

    Python 3.7
    PostgreSQL.
    Redis, if using Celery
    First things first.

* Create a virtualenv::

        $ python3.7 -m venv <virtual env path>
        
* Activate the virtualenv you have just created::

        $ source <virtual env path>/bin/activate
        
* Install development requirements::

    $ pip install -r requirements/local.txt
    $ pre-commit install

 .. note::

    the `pre-commit` exists in the generated project as default.
    for the details of `pre-commit`, follow the [site of pre-commit](https://pre-commit.com/).

* Create a new PostgreSQL database using createdb::

    $ createdb <what you have entered as the project_slug at setup stage> -U postgres --password <password>
    
  Note

 if this is the first time a database is created on your machine you might need an initial PostgreSQL set up to allow local connections     & set a password for the postgres user. The postgres documentation explains the syntax of the config file that you need to change.

* Set the environment variables for your database(s)::

    $ export DATABASE_URL=postgres://postgres:<password>@127.0.0.1:5432/<DB name given to createdb>
    # Optional: set broker URL if using Celery
    $ export CELERY_BROKER_URL=redis://localhost:6379/0
  
  Note
  Check out the Settings page for a comprehensive list of the environments variables.

  See also

  To help setting up your environment variables, you have a few options:

  create an .env file in the root of your project and define all the variables you need in it. Then you just need to have   
  DJANGO_READ_DOT_ENV_FILE=True in your machine and all the variables will be read.
  Use a local environment manager like direnv
  Apply migrations:

    $ python manage.py migrate
* See the application being served through Django development server::

    $ python manage.py runserver 0.0.0.0:8000





Settings
--------

Moved to settings_.

.. _settings: http://cookiecutter-django.readthedocs.io/en/latest/settings.html

Basic Commands
--------------

Setting Up Your Users
^^^^^^^^^^^^^^^^^^^^^

* To create a **normal user account**, just go to Sign Up and fill out the form. Once you submit it, you'll see a "Verify Your E-mail Address" page. Go to your console to see a simulated email verification message. Copy the link into your browser. Now the user's email should be verified and ready to go.

* To create an **superuser account**, use this command::

    $ python manage.py createsuperuser

For convenience, you can keep your normal user logged in on Chrome and your superuser logged in on Firefox (or similar), so that you can see how the site behaves for both kinds of users.

Type checks
^^^^^^^^^^^

Running type checks with mypy:

::

  $ mypy project_django

Test coverage
^^^^^^^^^^^^^

To run the tests, check your test coverage, and generate an HTML coverage report::

    $ coverage run -m pytest
    $ coverage html
    $ open htmlcov/index.html

Running tests with py.test
~~~~~~~~~~~~~~~~~~~~~~~~~~

::

  $ pytest

Live reloading and Sass CSS compilation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Moved to `Live reloading and SASS compilation`_.

.. _`Live reloading and SASS compilation`: http://cookiecutter-django.readthedocs.io/en/latest/live-reloading-and-sass-compilation.html




Email Server
^^^^^^^^^^^^

In development, it is often nice to be able to see emails that are being sent from your application. For that reason local SMTP server `MailHog`_ with a web interface is available as docker container.

Container mailhog will start automatically when you will run all docker containers.
Please check `cookiecutter-django Docker documentation`_ for more details how to start all containers.

With MailHog running, to view messages that are sent by your application, open your browser and go to ``http://127.0.0.1:8025``

.. _mailhog: https://github.com/mailhog/MailHog



Deployment
----------

The following details how to deploy this application.


Heroku
^^^^^^

See detailed `cookiecutter-django Heroku documentation`_.

.. _`cookiecutter-django Heroku documentation`: http://cookiecutter-django.readthedocs.io/en/latest/deployment-on-heroku.html



Docker
^^^^^^

See detailed `cookiecutter-django Docker documentation`_.

.. _`cookiecutter-django Docker documentation`: http://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html



