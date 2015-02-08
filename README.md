django-easy-avatar
==================
        
A super easy AJAX loading avatar for profile management.  django-easy-avatar is currently being used in production by Noob Media LLC for http://www.noobmovies.com

Example...
http://www.findgamersonline.com/user/profile/1/

django-easy-avatar needs jQuery for ajax file uploading and validation.  this plugin also uses Pillow for image manipulation and management.    

Video Tutorials are available!

http://www.youtube.com/watch?v=y1ndWIdK9WI&feature=youtu.be

This plugin is free to be adapted at GitHub;
https://github.com/chawk/django-easy-avatar

Written documentation is available at readthedocs.org

http://django-easy-avatar.readthedocs.org/en/latest/

==Instructions==

1.  pip install django-easy-avatar
2.  add easy_avatar to your installed apps
3.  add the below paths to your settings.py file (make sure you point to the right locations 
(example)
FILE_SAVE_PATH = "/root/path/to/your/static/avatars" ## must give apache or whatever webserver you're using write access to this directory
FILE_URL_PATH = "http://www.noobmovies.com/static/avatars/" ## your url where the uploaded image can be handled by your server
4.  Add 'django.core.context_processors.request' to your TEMPLATE_CONTEXT_PROCESSORS in your settings.py file. 
(example) 
TEMPLATE_CONTEXT_PROCESSORS = (
    ...
    'django.core.context_processors.request',
    ...
    )
5.  add (r'^avatar/', include('easy_avatar.urls')), to your urls.py file
6.  in the template where you plan on using django-easy-avatar add {% load avatar_tags %} to the top of the template
7.  to place the form in the page add the below
(example)
{% if request.user.is_authenticated and request.user.id == userProfile.user.id %}
        {% upload_form %}
{% else %}
        <img src="{{ avatar.image_url }}" width="100" height="100" alt="{{ userProfile.user.username }}" />
{% endif %}

If you have any troubles with this setup you will most likely be running into a permissions problem when your app tries to write the file to the directory.  
