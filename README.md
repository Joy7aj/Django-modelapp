pip install Django
django-admin startproject notable_django
cd notable_django
pip install django-tastypie
python manage.py startapp api
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'api'
]
class Note(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    class Note(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
def __str__(self):
        return self.title
class Note(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
def __str__(self):
        return '%s %s' % (self.title, self.body)
    python manage.py makemigrations
python manage.py migrate
python manage.py shell
>>> from api.models import Note
>>> note = Note(title="First Note", body="This is certainly noteworthy")
>>> note.save()
>>> Note.objects.all()

>>> exit()
>>> from tastypie.resources import ModelResource
from api.models import Note
class NoteResource(ModelResource):
    class Meta:
        queryset = Note.objects.all()
        resource_name = 'note'
>>> from django.conf.urls import url, include
from django.contrib import admin
from api.resources import NoteResource
note_resource = NoteResource()
urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^api/',include(note_resource.urls)),
]
python manage.py runserver
>>>
>>> from tastypie.resources import ModelResource
from api.models import Note
from tastypie.authorization import Authorization
class NoteResource(ModelResource):
    class Meta:
        queryset = Note.objects.all()
        resource_name = 'note'
        authorization = Authorization()
>>> from tastypie.resources import ModelResource
from api.models import Note
from tastypie.authorization import Authorization
class NoteResource(ModelResource):
    class Meta:
        queryset = Note.objects.all()
        resource_name = 'note'
        authorization = Authorization()
        fields = ['title', 'body']
>>> 
        

        
        
