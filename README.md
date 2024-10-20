# Ex.08 Design of Interactive Image Gallery
## Date:

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
### settings.py
~~~
ALLOWED_HOSTS = ['*']
~~~
### gallery.html
~~~
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="{% static 'gallery/styles.css' %}">
    <script src="{% static 'gallery/scripts.js' %}" defer></script>
    <title>Interactive Image Gallery</title>
</head>
<body>
    <h1>Interactive Image Gallery</h1>
    <div class="gallery">
        {% for image in images %}
            <img src="{{ image.image.url }}" alt="{{ image.title }}">
        {% endfor %}
    </div>
</body>
</html>

~~~
### Styles.css
~~~
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
}
.gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 10px;
}
.gallery img {
    margin: 10px;
    width: 200px; /* Adjust as needed */
    height: auto;
    transition: transform 0.3s;
}
.gallery img:hover {
    transform: scale(1.1);
}

~~~
### scripts.js
~~~
const images = document.querySelectorAll('.gallery img');
images.forEach(img => {
    img.addEventListener('click', () => {
        const src = img.getAttribute('src');
        const lightbox = document.createElement('div');
        lightbox.className = 'lightbox';
        lightbox.innerHTML = `<img src="${src}" alt="Lightbox Image">`;
        document.body.appendChild(lightbox);
        lightbox.addEventListener('click', () => {
            document.body.removeChild(lightbox);
        });
    });
});

~~~
### models.py
~~~
from django.db import models

class Image(models.Model):
    title = models.CharField(max_length=100)
    image = models.ImageField(upload_to='images/')

    def __str__(self):
        return self.title

~~~
### views.py
~~~
from django.shortcuts import render
from .models import Image

def gallery_view(request):
    images = Image.objects.all()
    return render(request, 'gallery/gallery.html', {'images': images})

~~~
### urls.py
~~~
from django.urls import path
from .views import gallery_view

urlpatterns = [
    path('', gallery_view, name='gallery'),
]

~~~

## OUTPUT:
![image](https://github.com/user-attachments/assets/3b02172a-1a32-4b53-bc67-42455893a65f)


## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
