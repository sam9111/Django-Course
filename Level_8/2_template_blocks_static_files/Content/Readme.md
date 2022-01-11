Template Inheritance is one of the most powerful features of Django's template engine, Template inheritance allows you to create a template skeleton that can be reused in other templates.

Most applications have a common header/footer/menu in all templates. This is where template inheritance comes in handy.

Let's learn more with an example :

let's create a base template called `base.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>{% block title %}Default Title{% endblock %}</title>
  </head>
  <body>
    <div>
      <ul>
        <li><a href="/">Home</a></li>
      </ul>
    </div>
    <div>{% block content %}{% endblock %}</div>
  </body>
</html>
```

This template can be used as a base template for other templates that we create, lets create a new template to list tasks from the base template.

```html
{% extends 'base.html' %} 

{% block title %}View Tasks{% endblock %} 

{% block content %}
<h1>All the content should go here!</h1>
{% endblock %}
```

For any child template, you must define which parent template you are extending from at the start of the file, we use the extends tag for extending a parent template, you can extend any template in Django,
Once we specify the parent template, we can create blocks we want to override/modify in the child template.

When rendering the page, Django will load up the parent template and replace the blocks with the child template. This means that anything that is not specified inside a block is ignored completely. This makes it really easy to structure web documents and makes it easier to reuse HTML code.

Templates in Django can do a lot more stuff, take a look [here](https://docs.djangoproject.com/en/4.0/ref/templates/language/) for the complete documentation.

### Static File Handling

Static files are files that are not changed when the application is running, these include the CSS files, images, javascript files, and any other type of files that are not dependent on the application logic.

Django provides a very simple way to handle static files. Let's first create a new folder called static at the root of our project. This folder will contain all the static files that are used in our application.

Let's add an image to our static folder, this could be any image, let's call it `test_image.png`

Now let's create a new template called `test_static.html` , and then create a route called `/test_static/` that renders this template.

To reference the static file inside a Django template, we need to let Django know that we are serving a static file and let it handle the route to the static file.

```html
{% load static %} <!-- This tag should be at the top of the HTML document and must only be defined once. -->
<img src="{% static 'test_image.png' %}" alt="Test Image">
```

Instead of manually specifying the URL route to the image, we are letting Django handle the URL creation, this way if decide on moving all static files to a separate server, we do not need to change all the static URL's in our template, we can let Django take care of it. Letting Django handle the static files also opens the door to a lot of packages to build more features on top.

This method is applicable to any static file, not just images, we can use the static tag to load our CSS files, js files, etc.

> Note that the load static tag has to be the first tag in the template and it should only be defined once.