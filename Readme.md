# Faker Higher Ed

## About

This is a collection of sample code and directions for creating plugins and providers for Snowfakery. We're trying to create fake data to make a whole university setup.
[EDA Data Dictionary](https://powerofus.force.com/s/article/EDA-Data-Dictionary) - please try to keep fields in use to standard Salesforce or EDA fields.

## Things you'll need

1. Python 3 (generally recent-ish version).
2. Snowfakery 1.9 or later.
3. Faker module for python (`pipx install Faker`).
4. A recipe to work from (see the [recipes folder of this repo](https://github.com/SFDO-Community-Sprints/Snowfakery-Recipe-Templates/tree/main/snowfakery_samples) for ideas).

## Creating a fakery provider for Snowfakery

1. Create a directory in your project to hold your plugins.
2. Create a file named `__init__.py` in that directory to make a package.
3. Create directory for your new provider with the pattern `faker_[my_service_name]`, in my case `faker_nonprofit`.
4. In the directory create a file named `__init__.py` this defines the faker provider module.
5. Create your provider in that file (see example for details):
    1. `import faker.providers` to make sure you have required classes.
    2. Define a series of dictionaries for providers creating text.
    3. Create a class that extends the base: `class Provider(faker.providers.BaseProvider):`
    4. Define a method that returns the desired values: `def nonprofit_name(self):`
6. Create `test.py` in your `plugins` directory.
7. Add tests to make sure it works cause it helps keep life easy (see example): `$ python -m plugins.test`

## Attach Your Provider to your recipe

1. Open the basic recipe you want to use for testing (start with something simple you already know how to use).
2. Add a new line at the top to load the new plugin: `- plugin: plugins.faker_highered`
3. Add/Update a field to use the new provider.
