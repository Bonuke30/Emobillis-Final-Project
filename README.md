# Charity connect

## INTRO
A membership website for charities written in Django.

Charity owners can create an account and add a profile for their charity. The site admin has to approve all charity organization profiles.

Once approved, the charity owner can login and create 'event' objects to tell the world about upcoming fundraising events.

## FEATURES
### Models and Fields
- CustomUser (extends AbstractUser) 
  - Standard user fields - username, email, is_staff
  - Extended user fields - charity name, charity address, charity postcode, charity website, charity bio, country (django-countries field), continent (choice field), charity image (pillow), approved (boolean field)
- Event - user (foreign key), name, description, date, url, image field, slug field, approved + date in future method

### Forms
- Site Login form
- Signup form
- CustomUserCreationForm
- CustomUserUpdateForm
- Profile update form
- Search events form
- Password reset form

### Site Admin
- Events - approve events
- Charity signups - approve charities

### Site Pages
- Index - description and site links including login/ logout/ signup links
- All Charities - paginated list
- All Events - paginated list
- Search Events
- LogIn/ LogOut
- Signup
- Password reset and confirmation
- Profile page - (logged in users)


## TOOLS 
- Django
- Bootstrap
- python-decouple
- django-countries
- Pillow
- Django registration, login and password reset system

### To Do
- [ ] Add custom user settings to the wagtail admin dashboard
- [ ] Add a news blog app
- DONE - Add a search events page - add to the menu
- [ ] Add a link to the main blog page to the menu

## SCREENSHOTS

### Homepage

## GETTING STARTED


```
virtualenv charity connect -p python3`
cd charityconnect
source bin/activate
pip install django
django-admin start charityconnect
cd charity connect
pip install -r requirements.txt
```

Set up a database table and assign priveliges.
Create a file called '.env' and add:
```
SECRET_KEY=12345etc.
DEBUG=True
DB_NAME=mysite
DB_USER=newusername
DB_PASSWORD=password
DB_HOST=127.0.0.1
PORT=3306
```

Install python decouple, any database client you require (MySQL example used here) 
```
pip install python-decouple
pip install mysqlclient
```

Install django-countries

`pip install django-countries`

See files in '/settings' dir to see how to set up python-decouple 'config', django-countries, abstract user and bespoke database.

```
python manage.py startapp accounts
python manage.py startapp events
```

**NOTE**: Setup custom user code from the app 'accounts' **before** the first migration:

Usual python web application creation
```
python manage.py makemigrations accounts
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

## RELATED
There is some debate over whether to use a Custom User model or to create a one-to-one field for a model called 'Profile' linked to a user.  

Here are some useful links that discuss the topic further: 

