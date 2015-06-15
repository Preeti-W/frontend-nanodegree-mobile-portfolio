## Project 5 Website Performance Optimization
There are two parts to this project. 
Part 1: Google PageSpeed score of 90 or higher on mobile and desktop for index.html
Part 2: 60fps should be obtained for the pizza.html page (views/pizza.html)

## Part 1
The keys to having a good Google PageSpeed score are to minimize the amount of bytes
that are needed for download, reduce the critical resources for rendering, and 
shorten Critical Rendering Path length.

I have inlined the font and style css files and put the 'async' tag on Google
analytics JS file because it isn't necessary for rendering the page therefore 
reducing CRP to one. I compressed the image "views/images/pizzeria.jpg"
because having an image that large is unnecessary when it only needs to be a
small image.

Next I used Grunt to reduce bytes by minify all of the necessary files for 
production.

Website: 
Website Google PageSpeed:

## Part 2
