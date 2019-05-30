# Project Details
  

## Requirements  and installation
   pip install djangorestframework



## Add this in installed apps in settings.py
       'rest_framework',
       'rest_framework.authtoken'


## in setting.py add this
      REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': (
        'rest_framework.authentication.TokenAuthentication',
    ),
    'DEFAULT_PERMISSION_CLASSES': (
        'rest_framework.permissions.IsAuthenticated', ) 
    }

## creating serializers.py in
   from django.contrib.auth.models import User

   from rest_framework import serializers

   class UserSerializer(serializers.ModelSerializer):
     class Meta:
         model = User
         fields = ('id', 'username', 'first_name', 'last_name', 'email')
## After creating serialize.py 
   post(self, request, format=None):
         serializer = UserSerializer(data=request.DATA)
         if serializer.is_valid():
             serializer.save()
             return Response(serializer.data, status=status.HTTP_201_CREATED)
         return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)

 
