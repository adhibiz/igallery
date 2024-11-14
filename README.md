# Ex.08 Design of Interactive Image Gallery
### Date: 29.10.2024

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
    <title>Image Gallery</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#gallery">Gallery</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main id="gallery">
        <div class="gallery-container">
            <img src="image1.jpg" alt="Image 1">
            <img src="image2.jpg" alt="Image 2">
            <img src="image3.jpg" alt="Image 3">
            <img src="image4.jpg" alt="Image 4">
            <img src="image5.jpg" alt="Image 5">
            <img src="image6.jpg" alt="Image 6">
            <img src="image7.jpg" alt="Image 7">
            <img src="image8.jpg" alt="Image 8">
            <!-- Add more images as needed -->
        </div>
    </main>

    <footer>
        <p>&copy; 2024 Your Website</p>
    </footer>
</body>
</html>


~~~
### Styles.css
~~~
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #333;
    color: white;
    padding: 10px 0;
}

nav ul {
    list-style: none;
    padding: 0;
    display: flex;
    justify-content: center;
}

nav ul li {
    margin: 0 15px;
}

nav ul li a {
    color: white;
    text-decoration: none;
}

.gallery-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    padding: 20px;
}

.gallery-container img {
    width: 100%;
    height: auto;
    border-radius: 8px;
}

footer {
    text-align: center;
    padding: 10px 0;
    background-color: #f1f1f1;
    margin-top: 20px;
}

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
