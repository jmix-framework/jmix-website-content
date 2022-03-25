# Application Settings

Provides a simple API and UI to work with mutable values of different types stored in database.

## Overview

The Application Settings add-on provides a simple API and UI to work with mutable values of different types stored in the database. These values are usually used as parameters of different functionality of the application.

Settings are defined by regular entities, the only requirement for them is to extend a specific base class. You can set default values of parameters using annotations on the settings entity class.

The API enables loading settings by the entity class and saving changed values. The add-on also provides a UI screen for managing settings at runtime.