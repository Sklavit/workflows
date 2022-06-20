---
description: >-
  Considering some text-based configuration and Python-based configuration there
  are options:
---

# Why configuration should be in Python



| Text-based | Python |
| :--- | :--- |
| \[Sections\] | May use classes for sections directly |
| var=value | `var=value` |
| ; or \# for comments | `# for comments` |
| NO hints | type hintsnaming hintsquick docs |
|  |  |
| CONS: no code at all can be executed | CONS: malitious code can be executed |
|  |  |

Python config used in some Python projects, i.e. Flask-based projects: 

```text
Config example from https://medium.freecodecamp.org/structuring-a-flask-restplus-web-service-for-production-builds-c2ec676de563
```



{% code-tabs %}
{% code-tabs-item title="config.py" %}
```python
"""
Config example from 
https://medium.freecodecamp.org/structuring-a-flask-restplus-web-service-for-production-builds-c2ec676de563
"""
import os

# uncomment the line below for postgres database url from environment variable
# postgres_local_base = os.environ['DATABASE_URL']

basedir = os.path.abspath(os.path.dirname(__file__))

class Config:
    SECRET_KEY = os.getenv('SECRET_KEY', 'my_precious_secret_key')
    DEBUG = False


class DevelopmentConfig(Config):
    # uncomment the line below to use postgres
    # SQLALCHEMY_DATABASE_URI = postgres_local_base
    DEBUG = True
    SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(basedir, 'flask_boilerplate_main.db')
    SQLALCHEMY_TRACK_MODIFICATIONS = False


class TestingConfig(Config):
    DEBUG = True
    TESTING = True
    SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(basedir, 'flask_boilerplate_test.db')
    PRESERVE_CONTEXT_ON_EXCEPTION = False
    SQLALCHEMY_TRACK_MODIFICATIONS = False


class ProductionConfig(Config):
    DEBUG = False
    # uncomment the line below to use postgres
    # SQLALCHEMY_DATABASE_URI = postgres_local_base
```
{% endcode-tabs-item %}
{% endcode-tabs %}

  
  


  




