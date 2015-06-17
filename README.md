## Project 5 Website Performance Optimization
There are two parts to this project.

Part 1: The starting sample portfolio has a low Google PageSpeed score. The 
goal is to get a Google PageSpeed score of 90 or higher on mobile and desktop
for index.html

Part 2: The file "views/pizza.html" isn't optimized for 60fps. The goal is to
optimize it to 60fps.

## Part 1
I have inlined the font and style css files and put the 'async' tag on Google
analytics JS file because it isn't necessary for rendering the page therefore 
reducing CRP to one. I used ImageMagick to compress the images "views/images/pizzeria.jpg" 
and "img/profilepic.jpg" and used Grunt's tools to minify all of the necessary files to
reduce the amount of bytes that needed to be downloaded.

Website: http://micyang.github.io/frontend-nanodegree-mobile-portfolio/

Speed Test: https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fmicyang.github.io%2Ffrontend-nanodegree-mobile-portfolio%2F


## Part 2
One of the major bottlenecks is in a function called updatePositions(). In the for
loop, it calculates phase 200 times when it only calculates 5 unique values. In
order to solve this duplicity problem, the phase calculation is calculated outside the
for loop and stored in an array for access.

Replaced a slow method to access the DOM, document.querySelectorAll(), with a 
faster method, document.getElementsByClassName().

In updatePositions(), the function accesses the DOM with the class name 'mover'
every time the user decides to scroll. The 'items' variable never changes. It
only needs to access the DOM once. It is moved into the global scope for 
updatePositions() to use.

For the eventListener 'DOMContentLoaded', in the for loop, 200 pizzas aren't
seen in rendering. I dynamically create the pizza amount based on height of user's
web browser.

To reduce painting, I used transform translateZ and translate3d and backface-visibility hidden
CSS properties to have them in their own seperate layers.

In changePizzaSizes(size) function, the variables dx and newwidth don't need to
be iterated in the for loop because it's all the same width. The variables were
put outside the for loop to reduce time. Created a local variable randomPizzaContainer
to store the elements by class name randomPizzaContainer to decrease the amount of
times it needs to access the DOM.

Website: http://micyang.github.io/frontend-nanodegree-mobile-portfolio/views/pizza.html

## Setup locally (from original README)
1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```
1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights!
