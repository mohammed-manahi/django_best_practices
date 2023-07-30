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
   * Use Docker to unify local development environments for everyone. 