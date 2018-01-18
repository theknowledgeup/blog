---
author: Ranvir Singh
comments: true
date: 2018-01-18 06:28:30.772986
layout: post
title: How to use FactoryBoy to create model instances in python for testing
slug: how-to-use-factoryboy-to-create-model-instances-in-python-for-testing
---
Testing is one of the basic&nbsp;and most important things&nbsp;that are needed to be done. Also, it is&nbsp;one of the most important developmental phases. I have already discussed testing in one of my earlier posts. In that post, I talked about the way in which we can write tests for models. Today I am going to talk about using FactoryBoy for testing Django application.&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
The name 'Factory Boy' is inspired by the Factory Girl testing tool for&nbsp;Ruby on Rails. Without Factory boy, you have to write a lot of code for the creation of test cases. For writing test, you have to spend a lot of time writing the setup method for the tests.

Without the use of factories, this is how your tests will look like:

&nbsp;

`` from django.test import TestCase ``

`` from my_app.models import Person ``

`` class DataBaseStore(TestCase): ``

`` &nbsp; &nbsp; def setUp(self): ``

`` &nbsp; &nbsp; &nbsp; &nbsp; # Creating all the models&nbsp; ``

`` &nbsp; &nbsp; &nbsp; &nbsp; Person.objects.create(gender='male', age=20, name='ranvir') ``

`` &nbsp; &nbsp; def test_something(self): ``

`` &nbsp; &nbsp; &nbsp; &nbsp; # test all the things that you want to. ``

&nbsp;

On the other hand, it is always nice to separate your setting up stuff from the main stuff. For this sometimes we have to write long code in the beginning which helps us in the future by allowing us to write smaller code in the future.&nbsp;

We can write factories anywhere but it's always a good idea to write it in a file named factories.py inside the root directory of your app.

Write following in the factories.py file inside your root directory.

&nbsp;

`` from factory.django import DjangoModelFactory ``

`` from my_app.models import Person ``

`` class PersonFactory(DjangoModelFactory): ``

`` &nbsp; &nbsp; class Meta: ``

`` &nbsp; &nbsp; &nbsp; &nbsp; model = Person ``

`` &nbsp; &nbsp; name = 'ranvir' ``

`` &nbsp; &nbsp; age = 20 ``

`` &nbsp; &nbsp; gender = 'male' ``

&nbsp;

Now we can simply call these factories during the test generation and create as many instances of models as we want to. This is a pretty simple case but we really can do a lot more. We can create instances of varies types by making use of FuzzyText and Sequence.

Hope you guys liked the idea of the post. We really can do a lot of stuff using this library. Do share your views regarding this post if you have used factories in the past or want to use it in your project.