# django-orm-standalone
Django ORM Standalone

## Settings

Editar archivo settings.py y habilitar la conexion para el motor que usara.

Se debe instalar el paquete necesario para cada motor

## Models

Para crear modelos se deben agregar en el archivo models.py

~~~python
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(max_length=255)
    grupo = models.ManyToManyField('Group')

class Group(models.Model):
    name = models.CharField(max_length=255)
~~~

## Migrate

Migrar los modelos creados o modificados

~~~
$ source ENV/bin/activate
(ENV) $ python manage.py makemigrate
(ENV) $ python manage.py migrate
~~~

## Example

Ejemplo de uso

~~~python
import orm
orm.Orm()

from data.models import User, Group
obj_grupo, created = Group.objects.get_or_create(name='GrupoEjemplo')
User.objects.create(name='Jose', email='example@domain.com', grupo=obj_grupo)
user = User.objects.all()[0]
print user.name
print user.grupo_set[0].name
~~~

### Develop

@francisco

