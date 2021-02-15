# Miguel Camacho Stream Four Project: 
# Fullstack Development Milestone Project - Code Institute 
**This is for educational use.**

MileStone 4 Full Stack Software Development Course at Code Institute. Visit [gitRepo](https://github.com/MACmidiDEV/MCAMACHO-DataCentric-CIM3) for entire build information. The main focus of this project was to create, develop, test and deploy a postgres database configured Django web app configured to Amazons Web Servers allowing application users to create secure profiles and order services via Stripe API intergration and host it on [Heroku](https://little-links-learning.herokuapp.com/)
Came home and media e-commerce web application Was designed to showcase all services provided by a fully licensed insured Rhode Island general contractor

the mission is to provide existing and potential clients with a place to Review all services provided and even pay do you have that service performed within the web application review all services provided and even pay do you have that service performed within the web application The visiom is to remodel the perfect space for your home One client and service at a time.

With ease-of-use in mind a lot of the features that are native to the to Django admin site were implemented within the site UI to keep styling consistent and quick modifications to the site readily available Important disclaimer although this project us can team real services please be advised that this website is for educational purposes only stripe API is implemented with configured testing credentials 

Credit card testing transaction credentials:
* **Credit Card :** 4242 4242 4242 4242
* **Expiration date :** 04 / 24
* **CVC :** 424
* **ZIP :** 42424

## Table of Contents

  * [**UX - research and goals**](#ux---Customer-|-Business-goals)
    + [Business Goals](#business-goals)
    + [Customer Goals](#customer-goals)
  * [**Features and App Sections**](#features-and-app-sections)
    + [Web App Sections](#web-app-sections)
    + [Features and Django Apps](#features-and-django-apps)
    + [Features Left to Implement](#features-left-to-implement)
    + [Wireframes](#wireframes)
  * [**Information Architecture**](#information-architecture)
    + [Data Models](#data-models)
  * [**Technologies Used**](#technologies-used)
    + [Media](#media)
    + [Acknowledgments](#acknowledgments)

## UX - Customer | Business goals

### Business Goals

As an e-commerce site owner...

* I want the users to be comfortable with my platform.
* I want to offer a shopping experience shoppers trust.
* I want to have a marketplace offering more than just service.
* I want to be able to make changes on the inventory myself.

### Customer Goals

As a customer...

* I want to buy from a company i can trust to get it done
* I want to read more about the company so that I see if the company's values match mine.
* I want to have information about the services I'm buying easily available.
* I want to be able to filter the services.
* I want to be able to store my shipping details so that it’s easier for me to check out.
* I want to be able to see my orders so that I can track what I buy and spend money on.

As a loyal customer...

* I want to get a deal on shipping
* To track prior orders

## Features and App Sections

### Web App Sections

1. **Navigation at the top** - top nav fixed and responsivene throught app
1. **Homepage** - intro app overview of company
1. **Ecomm** - e-commerce list of services sort and filter by category name and service tag. link to service details and adds to bag for purches 
1. **Service page** - a page dedicated to individual service displays all information 
1. **About page** - brief company info 
1. **User account** - available to only registered and logged in users with the purpose of back tracking order history details
1. **Admin account** - available users with admin rights with the purpose of having access to the orders, user profiles, as well as service and blog inventory. Majority of the information is stored in [the Django admin site](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/) but the users can also do common tasks such as adding, editing and deleting services or blog posts through ECOSiO's UI.
1. **Footer** - ri general contractors registraion number and link to about page 

### Features and Django Apps
[Django project](https://docs.djangoproject.com/en/3.1/ref/applications/), consists of 6 Django applications listed below. 

* `about`
* `bag`
* `checkout`
* `home`
* `profiles`
* `services`

**Navigation**
* always present on the top so that the users are able to navigate themselves anytime. It consists of **the top navigation** 

**Search functionality**
* it allows customers to enter keywords associated with the services they wish to purchase.
* the search results are displayed as a feed of services by using the page templates prepared for the `services` Django app (i.e. ecomm).
* the search results show the number of services found for the search query, as well as inform the user if no services were found along with a CTA linked to the ecomm's feed.

**Breadcrumbs**
* breadcrumbs are present throughout the `services` pages `bag` and `checkout` Django apps and the `profiles` app.
* purpose of this feature is to ease the navigation 

**Toasts**
* 4 main categories: `toast_success`, `toast_info`, `toast_warning` and `toast_error`.
* they appear on every page whenever a certain action has been done by the user.
* their purpose is to give feedback on the action a user has just performed,

**Django-allauth feature**
* `django-allauth` is a Python package. As written in the [django-allauth docs](https://django-allauth.readthedocs.io/en/latest/), it is an "integrated set of Django applications addressing authentication, registration, account management as well as 3rd party (social) account authentication."
* it provides a set of features such as **signup**, **login**, **logout** and **password change**.
* after signing up, a verification e-mail is sent to the registered e-mail to confirm it. Once confirmed, the user can log in with their credentials and access the `profiles` app.

**Automatic e-mails**
* a company gmail account **camhomemedia@gmail.com** configured to be sender for all verification, reset and confirmation e-mails.
* users receive an **order confirmation e-mail** after a purchase, **account verification e-mail** after the registration, **password reset e-mail** after requesting a password reset.

**Homepage app**
* `homepage` Django app serving as landing page
* displays info about services provided

**About app**
* `about` Django app displays brief info on company


**services app**
* `services` Django app is where all the logic and templates connected to the service 

**filters for sorting services** (A-Z, Z-A, price low-high, price high-low)

**service pages** are pages dedicated to each individual service. On these pages, the users can view all details on service

**bag app**
* `bag` Django app is a standard e-commerce functionality which assists the checkout process.
* a bag is always present in the top right corner of the web app. 

* after clicking on the bag in the top right corner, the user gets an overview of all the services put into the bag. The user can also modify the quantity of the added services as well as remove the service.


**Checkout app**
* `checkout` Django app is another standard e-commerce functionality which enables users to buy the services online from the ecomm.
* in order to check out, the user is presented with a **form asking for the shipping and payment details** and with the **overview of the order**.

Logged in users will have an option to **save their information** to the profile which should populate the form with relevant details for the next purchase.

* a webhook is implemented to the `checkout` so that the order is successfully processed in case the checkout process gets interrupted. Some reasons might be closing the browser too soon or losing internet connection.
* "payments" are handled through `stripe`. A test purchase can be made with the following details:
    * **credit card:** 4242 4242 4242 4242
    * **expiration date:** 04 / 24
    * **CVC:** 424
    * **ZIP:** 42424
* after the payment has been processed, the user is presented with the order summary on the **order confirmation page**.
* logged in buyers can also see their **order history** on the `profiles` pages.

**Profiles app**
* `profiles` Django app is available to registered, authenticated users.
* it offers 2 features: **order history**, **saving shipping information** 
* **order history** displays all previous orders per user account.
* **saving shipping information** is done through a form which can be edited anytime. This information is what populates the checkout form for the next orders and where shipping information saved during the checkout process is stored.

### Features Left to Implement

**Animations**
* the project's UI could be further enhanced via animations.

### Surface
modern design apporache 

## Information Architecture
PostgreSQL database 


### Data Models
configured to database

**User Model**

Django `User` model is a part of Django’s authentication system `django.contrib.auth.models`. You can read more about its fields, attributes,
methods, etc. [here](https://docs.djangoproject.com/en/3.0/ref/contrib/auth/).

**Profiles App**

`UserProfile` model
    user = models.OneToOneField(User, on_delete=models.CASCADE) 
    default_phone_number = models.CharField(max_length=20, null=True, blank=True)

    default_country = CountryField(blank_label='Country *', null=True, blank=True)

    default_postcode = models.CharField(max_length=20, null=True, blank=True)

    default_town_or_city = models.CharField(max_length=40, null=True, blank=True)

    default_street_address1 = models.CharField(max_length=80, null=True, blank=True)

    default_street_address2 = models.CharField(max_length=80, null=True, blank=True)

    default_county = models.CharField(max_length=80, null=True, blank=True)

**Services App**

`Category` model
    name = models.CharField(max_length=254)

    friendly_name = models.CharField(max_length=254, null=True, blank=True)
        
`Service` model

    category = models.ForeignKey('Category', null=True, blank=True, on_delete=models.SET_NULL)

    sku = models.CharField(max_length=254, null=True, blank=True)

    name = models.CharField(max_length=254)

    description = models.TextField()

    price = models.DecimalField(max_digits=6, decimal_places=2)

    rating = models.DecimalField(max_digits=6, decimal_places=2, null=True, blank=True)

    image_url = models.URLField(max_length=1024, null=True, blank=True)

    image = models.ImageField(null=True, blank=True)
    

**Checkout App**

`Order` model

    order_number = models.CharField(max_length=32, null=False, editable=False)

    user_profile = models.ForeignKey(UserProfile, on_delete=models.SET_NULL, null=True, blank=True, related_name='orders')

    full_name = models.CharField(max_length=50, null=False, blank=False)

    email = models.EmailField(max_length=254, null=False, blank=False)

    phone_number = models.CharField(max_length=20, null=False, blank=False)

    country = CountryField(blank_label='Country *', null=False, blank=False)

    postcode = models.CharField(max_length=20, null=True, blank=True)

    town_or_city = models.CharField(max_length=40, null=False, blank=False)

    street_address1 = models.CharField(max_length=80, null=False, blank=False)

    street_address2 = models.CharField(max_length=80, null=True, blank=True)

    county = models.CharField(max_length=80, null=True, blank=True)

    date = models.DateTimeField(auto_now_add=True)

    delivery_cost = models.DecimalField(max_digits=6, decimal_places=2, null=False, default=0)

    order_total = models.DecimalField(max_digits=10, decimal_places=2, null=False, default=0)

    grand_total = models.DecimalField(max_digits=10, decimal_places=2, null=False, default=0)

    original_bag = models.TextField(null=False, blank=False, default='')

    stripe_pid = models.CharField(max_length=254, null=False, blank=False, default='')

`OrderLineItem` model

    order = models.ForeignKey(Order, null=False, blank=False, on_delete=models.CASCADE, related_name='lineitems')

    service = models.ForeignKey(Service, null=False, blank=False, on_delete=models.CASCADE)

    service_size = models.CharField(max_length=2, null=True, blank=True)

    quantity = models.IntegerField(null=False, blank=False, default=0)

    lineitem_total = models.DecimalField(max_digits=6, decimal_places=2, null=False, blank=False, editable=False)

### Wireframes

## Technologies Used

This project mostly focuses on the following technologies:

1. [HTML](https://en.wikipedia.org/wiki/HTML) - for creating the layout and the structure of the website
1. [CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) - for styling the website’s HTML code
1. [Bootstrap](https://getbootstrap.com/) - for additional styling and adding responsiveness to the website
1. [JavaScript](https://en.wikipedia.org/wiki/JavaScript) and [jQuery](https://jquery.com/) - for frontend interactivity
1. [Python](https://en.wikipedia.org/wiki/Python_(programming_language)) - for backed logic and structure
1. [Jinja](https://jinja.palletsprojects.com/en/2.11.x/) - for displaying backend information in frontend
1. [Django](https://www.djangoproject.com/) - high-level Python web framework
1. [Heroku](https://www.heroku.com/) - cloud platform where the web app is deployed
1. [SQLite](https://www.sqlite.org/index.html) - default Django's database used in development
1. [PostgreSQL](https://www.postgresql.org/) - production database through Heroku
1. [AWS S3](https://aws.amazon.com/) - for hosting media and static files on cloud
1. [Git](https://git-scm.com/) - for version control
1. [Stripe](https://stripe.com/en-gb-de) - for managing (test) transactions
1. [jQuery](https://jquery.com/) - dependency
1. [Popper.js](https://popper.js.org/) - dependency
1. [JavaScript](https://en.wikipedia.org/wiki/JavaScript) - code logic
1. [Gitpod](https://gitpod.io/) - for writing, editing and live previewing the code during the creation process
1. [GitHub](https://github.com/) - for hosting the project's repository
1. [Google Fonts](https://fonts.google.com/) - for selecting the fonts
1. [Favicon](https://favicon.io/) - for creating browser tab icons

## Media
All photos were taken from [unsplash](https://www.unsplash.com/), open source image library.

## Acknowledgements
All skills acquired from [codeInstitute](https://codeinstitute.net/), training source.
- [W3Schools](https://www.w3schools.com/python/python.asp)
- [mongoDB Documentation](https://docs.mongodb.com/manual/reference/method/db.collection/)
- [PyMongo Documentation](https://api.mongodb.com/python/current/api/pymongo/collection.html)
- [Stackoverflow](https://stackoverflow.com/)
- [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/)
