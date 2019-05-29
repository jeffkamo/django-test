# Getting started

```bash
python manage.py runserver
```

Visit http://127.0.0.1:8000/

If there is an error that claims `polls` is missing, you'll need to install my `django-polls` app.

```bash
# I had to use pip3 instead of pip to get this to work
pip3 install --user path/to/django-polls/dist/django-polls-0.1.tar.gz
```


# Migrations

After changing a model, database migrations will need to be generated and applied.

```bash
python manage.py makemigrations polls
python manage.py migrate
```

To preview what sort of database query is generated by any given migration, run (replacing `0001` with the migration number of your choice)...

```bash
python manage.py sqlmigrate polls 0001
```


# Shell sandbox

Import modules, apps and models to fiddle with them.

```bash
python manage.py shell
```

For example, test adding, updating and deleting items from the database via models.

```bash
python manage.py shell
>>> from polls.models import Question
>>> from django.utils import timezone
>>> q = Question(question_text="What's up?", pub_date=timezone.now())
>>> q.save()
>>> q.choice_set.create(choice_text='The sky', votes=0)
>>> c = q.choice_set.create(choice_text='Just hacking again', votes=0)
>>> c.delete()
>>> q.choice_set.count()
```


# Admin

After rulling `runserver` (as above in "Getting started"), visit at http://127.0.0.1:8000/admin/

Create a user with:

```bash
python manage.py createsuperuser
```


# Takeaways

I got to familiarized myself with...

- Django's project structure
- General workflow
- Customizing the Admin interface
- The relationship between models, views and templates
- How to make and apply database migrations
- How to handle basic HTTP requests
- Django's routing system via `urlpatterns`
- How to apply relative links without hardcoding URL paths
- How to render simple HTML pages
- How to create custom Django packages, and install them
