* General Coding Style:
	* Avoid abbreviating variable names.
	* Use PEP8 style guide.
	* Document classes and methods.
	* Write fat models, utility modules and thin views.
	* Maintain the 79-character limit.
	* Follow the standard import grouping: standard Python library imports, core Django framework import, third-party libraries imports, then local application imports.
	* Use absolute import when importing from outside the current app and explicit relative import when importing from another module in the current app.
	* Avoid using import *, import only needed modules, classes or methods.
    * Avoid naming collision of modules, use aliases to overcome the collision.
    * Use hyphens for URL patterns and underscores for URL pattern names.

* Django Environment Setup:
   * PostgreSQL is the preferred database to work with in development and production environments.
   * Use virtual environment for Django projects.
   * The recommended installation of Django is to use pip and requirements file.
   * Use Docker to unify local development environments for everyone when the team uses multiple operating systems and configuration environments. 

* Project Layout Configuration:
   * The preferred project layout is to place a root directory and inside it <configuration_root> and <django_project_root>.
   * Avoid including virtual environment directory to GitHub repository.
   * Save Python package usages into requirements file (pip freeze > requirements.txt).
   * Cookiecutter can be used for advanced project setup and boilerplate code creation.

* Fundamentals of Django App Design:
   * The philosophy of app design in Django is that "each app should be tightly focused on its task" which implies that the app has to do one thing and do it well.
   * App naming convention preference is to keep app name a single word, all in lowercase and the name should be plural expect for certain cases.
   * It is better to have many small apps than to have a few giant apps.

* Settings and Requirements File Configurations:
   * All settings files need to be version-controlled using a VCS except for secret keys and API credentials. 
   * Use multiple settings files for base, local, staging, testing, and production environments in a settings directory.
   * Each settings module should have its own corresponding requirements file with identical name to settings file name inside requirements directory.
   * Run commands for specific settings configuration, for example to run server for local settings: python manage.py runserver --settings=config.settings.local.
   * The official Django documentation encourages django-admin rather than manage.py when working with multiple settings files.