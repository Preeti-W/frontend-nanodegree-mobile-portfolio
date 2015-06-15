## Project 5 Website Performance Optimization
There are two parts to this project.

Part 1: The starting sample portfolio has a low Google PageSpeed score. The 
goal is to get a Google PageSpeed score of 90 or higher on mobile and desktop
for index.html

Part 2: The file "views/pizza.html" isn't optimized for 60fps. The goal is to
optimize it to 60fps.

## Part 1
The keys to having a good Google PageSpeed score are to minimize the amount of 
bytes that are needed for download, reduce the critical resources for rendering
and shorten Critical Rendering Path length.

I have inlined the font and style css files and put the 'async' tag on Google
analytics JS file because it isn't necessary for rendering the page therefore 
reducing CRP to one. I used ImageMagick to compress the images 
"views/images/pizzeria.jpg" and "img/profilepic.jpg" and used Grunt to minify all 
of the necessary files for production.


## Part 2
