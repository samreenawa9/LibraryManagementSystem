# LibraryManagementSystem
I started learn Django and working on "Library Managment system" as my first project.

#First of all, by using following command, created new Django Project
django-admin startproject library_system
cd library_system

#Created a Django App Inside the Project:
python manage.py startapp library

#After Adding the App to settings.py, I Planned my Requirements,What features the Library System will have:
Add Book
Issue Book
Return Book
Show available books
Track issued books

#then Designed the Database Schema and createed Models in models.py:
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)
    available = models.BooleanField(default=True)

class Student(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    roll_number = models.CharField(max_length=20)

class Issue(models.Model):
    book = models.ForeignKey(Book, on_delete=models.CASCADE)
    student = models.ForeignKey(Student, on_delete=models.CASCADE)
    issue_date = models.DateField(auto_now_add=True)
    return_date = models.DateField(null=True, blank=True)


#Migrated and Created Admin Panel:
python manage.py makemigrations
python manage.py migrate
#Registerd on admin.py:
from .models import Book, Student, Issue
admin.site.register(Book)
admin.site.register(Student)
admin.site.register(Issue)

#RUn server using:
python manage.py runserver

