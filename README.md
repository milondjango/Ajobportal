# from django.contrib import admin
# from django.urls import path,include
# from django.conf.urls.static import static
# from django.conf import settings
# from django.urls import re_path
# from django.views.static import serve

# urlpatterns = [
#     path('admin/', admin.site.urls),
#     path('',include('JobApp.urls')),
# ]
# urlpatterns+=re_path(r'^static/(?P<path>.*)$', serve, {'document_root': settings.STATIC_ROOT}),
# urlpatterns+=re_path(r'^media/(?P<path>.*)$', serve, {'document_root': settings.MEDIA_ROOT}),

#forms.py

# from django import forms
# from .models import *
# from django.contrib.auth.forms import UserCreationForm,AuthenticationForm


# class UserRegisterForm(UserCreationForm):
#     class Meta:
#         model = UserModel
#         fields = ['username','display_name', 'email','user_type', 'password1', 'password2']
        
        
    
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'
    
        
     


# class UserLoginForm(AuthenticationForm):
#     class Meta:
#         model = UserModel
#         fields = ['username', 'password1']
        
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'
        


# class JobSeekerForm(forms.ModelForm):
#     class Meta:
#         model = JobSeekerModel
#         fields = "__all__"
#         exclude = ['user']
        
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'

# class RecruiterForm(forms.ModelForm):
#     class Meta:
#         model = RecruiterModel
#         fields = "__all__"
#         exclude = ['user']
        
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'

# class JobForm(forms.ModelForm):
#     class Meta:
#         model = JobModel
#         fields = "__all__"
#         exclude = ['user']
        
        
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'
         

# class SkillForm(forms.ModelForm):
#     class Meta:
#         model = SkillModel
#         fields = "__all__"
        
#     def __init__(self, *args, **kwargs):
#         super().__init__(*args, **kwargs)
        
#         for i_name, i in self.fields.items():
#          i.widget.attrs['class'] = 'form-control'

# models.py

# from django.db import models
# from django.contrib.auth.models import AbstractUser

# # Create your models here.

# class UserModel(AbstractUser):
#     USER_TYPE = [
#         ('JobSeeker', 'JobSeeker'),
#         ('Recruiter', 'Recruiter')
#     ]
#     display_name = models.CharField(max_length=100)
#     user_type = models.CharField(max_length=100, choices=USER_TYPE)

#     def __str__(self):
#         return self.username
    

# class RecruiterModel(models.Model):
#     user = models.ForeignKey(UserModel, on_delete=models.CASCADE)
#     name = models.CharField(max_length=100, null=True, blank=True)
#     company_name = models.CharField(max_length=100, null=True, blank=True)
#     address = models.CharField(max_length=100, null=True, blank=True)
#     contact = models.CharField(max_length=100, null=True, blank=True)
#     profile = models.ImageField(upload_to='media/profile', null=True, blank=True)

#     def __str__(self):
#         return self.name
    
# class SkillModel(models.Model):
#     name = models.CharField(max_length=100)

#     def __str__(self):
#         return self.name or "Unnamed Skill"

# class JobSeekerModel(models.Model):
#     user = models.ForeignKey(UserModel, on_delete=models.CASCADE)
#     name = models.CharField(max_length=100, null=True, blank=True)
#     address = models.CharField(max_length=100, null=True, blank=True)
#     contact = models.CharField(max_length=100, null=True, blank=True)
#     skill = models.ManyToManyField(SkillModel)
#     resume = models.FileField(upload_to='media/resume', null=True, blank=True)

#     def __str__(self):
#         return self.name

# class JobModel(models.Model):
#     CATAGORY = [
#         ('Full Time', 'Full Time'),
#         ('Part Time', 'Part Time'),
#         ('Internship', 'Internship')
#     ]
#     user = models.ForeignKey(RecruiterModel, on_delete=models.CASCADE)
#     title = models.CharField(max_length=100)
#     catagory = models.CharField(max_length=100, choices=CATAGORY)
#     description = models.TextField()
#     skills = models.ManyToManyField(SkillModel)

#     def __str__(self):
#         return f"{self.title}"
    

# class ApplyJobModel(models.Model):
#     STATUS = [
#         ('Pending', 'Pending'),
#         ('ShortList', 'ShortList'),
#         ('Rejected', 'Rejected')
#     ]
#     job = models.ForeignKey(JobModel, on_delete=models.CASCADE)
#     job_seeker = models.ForeignKey(JobSeekerModel, on_delete=models.CASCADE)
#     status = models.CharField(max_length=100, choices=STATUS)



