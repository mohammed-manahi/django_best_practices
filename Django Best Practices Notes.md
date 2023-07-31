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

* Model Best Practices:
   * The ideal number of models in an app is five to 10 models.
   * Django provides three ways to do model inheritance: abstract base classes, multi-table inheritance, and proxy models.
   * Abstract base classes: tables are only created for derived models.
   * Multi-table inheritance: tables are created for both parent and child. An implied OneToOneField links parent and child.
   * Proxy models: a table is only created for the original model.
   * It is recommended to avoid Multi-table inheritance since it adds both confusion and substantial overhead.
   * Custom model managers are excluded by default by Django migrations, to include custom managers the following statement should be set in the custom manager: "use_in_migrations = True".
   * Custom model's save and delete methods won't be called when called by RunPython.
   * It is recommended to always back up your data before running a migration.
   * It is recommended to include migrations directory in VCS to be version-controlled.
   * Model design principles:
      * Setting null and blank options: null is database-related field option while blank is related to Django forms.
      * Using BinaryField: BinaryField is for raw data such as raw sensor data, it may affect database performance and can be replaced with FileField when it becomes a bottleneck.
      * Try to avoid using Generic Relations: Generic Relations are usually more trouble than they are worth.
      * Use choices and sub-choices model constants. 
      * Using custom model manager: when using custom model manager always set default model manager on top and then the custom model manager.
      * Keep fat models, thin views and use helper functions.

* Django's ORM:
   * Use get_object_or_404() instead of get() when querying single object and beware that it only works for views.
   * Do not use try-except block with get_object_or_404() because it already does that.
   * ObjectDoesNotExist can be applied to any model object while DoesNotExist is for a specific model.
   * When expecting one object but the query return more than one, check for MultipleObjectsReturned exception.
   * Try to avoid chaining too much functionalities when querying ORM, instead break complex query into multiple simple query and combine them together.
   * The Q function in Django's ORM provides logical expressions between conditions, while the F function allows to refer to a model field's value and use it in database queries.
   * Avoid raw SQL statements until it is necessary.
   * Add indexes as need in the meta class of the model.
   * Use ORM transactions when two or more database operations are contained in a single unit of work.

* Function And Class-Based Views:
   * The class-based views are more recommended to use except for custom error views or complicated ones in which function-based views are better.
   * Keep URLConf and views loosely coupled by avoiding logic inside URLConfs.
   * Use namespaces in URLConf for views.
   * Avoid using locals() as a view context since it makes the context of the view vague.

* Function-Based Views Best Practices:
   * The function-based views are simpler to work with, yet it provides less code reusability.
   * Avoid nested complex if-blocks as possible.
   * Use decorators using functools.wraps() when needed to avoid obfuscation.

* Class-Based Views Best Practices:
   * Class-based views use as_view() class method to return the callable view.
   * Use Mixins with class-based views: When using Mixins in Django class-based views, the base view classes always go the right in the method declaration and Mixins to the left.
   * The most common General class-Based Views (GCBV) are TemplateView, ListView, DetailView, FormView, CreateView, UpdateView, and DeleteView.
   * Use the view object itself to provide access to properties and methods that can be called by other methods and properties.

* Forms Best Practices:
   * Always use CSRF protection with HTTP forms that modify data. 
   * Use clean(), clean_<field_name>() and save() to have additional form instance attributes.

* Templates Best Practices:
   * Keep templates mostly in templates directory.
   * Do not write logic that perform operations in database layer inside the template, instead write it in the views and send it simplified to the templates. 

* Django REST Framework:
   * Django REST Framework supports function-based views and class-based view, however it is more common to use class-based views.
   * Place all API components into a package within an app in a directory called api/.
   * It is a good practice to abbreviate the urls of an API with the version number.
   * It is a good practice to use rate limiting in a REST API.