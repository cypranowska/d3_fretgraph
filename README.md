# d3_fretgraph
D3 tutorial for building an animated line graph (with real FRET data) for The Hacker Within at UC Berkeley on February 28, 2017.

# How to prepare for this tutorial

1. [Download and install Brackets](http://brackets.io/)
  * (This is Caroline's preferred tool for building visualizations with D3, but isn't strictly necessary. It has a nice live preview feature that is handy if you're building these visualizations to go on a webpage.)
2. Fork this repository
  * It has a template in the main directory that we'll use to write our code, our raw data in a .csv file in the /data directory, a minified version of D3 in the /d3 directory, and a finished version of the visualization in the /finished_version directory
  
# What is D3?

D3 stands for data-driven documents, and is a JavaScript library for building interactive data visualizations to display on the web. It was developed primarily by Mike Bostock, his PhD adviser, Jeffrey Heer, and Vadim Ogievetsky ([Bostock, Ogievetsky & Heer, IEEE Trans. Visualization & Comp. Grapics, 2011](http://vis.stanford.edu/files/2011-D3-InfoVis.pdf)). 

D3 is notoriously challenging because it requires knowing a bit about JavaScript, a bit about HTML/CSS, and a bit about SVG. The goal with this workshop is to help you get a good enough sense of how D3 works to explore on your own.

# D3 visualizations are built around binding data to HTML or SVG elements

What the heck does binding even mean? The idea here is that if you have a bunch of data and you want to use those data to manipulate elements on your webpage, then you need a way to select those elements and associate (or 'bind') your data to them. 

Here's an example of how to do this:

```javascript
var  sample = [1,2,3,4];

d3.select('body').selectAll('p')  // this selects all paragraph elements within the body of your HTML file, if you don't have                                      any <p> elements on your page then this is a virtual selection
  .data(sample)                   // this binds your data variable to your selection
  .enter()                        // THIS is the magic of D3! This method allows you to create NEW elements on the webpage                                          based on your data
  .append('p')                    // for each datum in your variable, D3 will append a new <p> element to your page
  .text("I'm a paragraph!");      // the text in each newly created <p> element
  
```
If you were to put this code between `<script>` tags on an HTML document and then view on a browser, you would see a page with 4 `<p>` elements with 'I'm a paragraph!' in them. But if you were to open your web inspector and run `console.log(d3.selectAll("p"))` you will see that each element has a `__data__` parameter, and that value will correspond to the value in `sample`. 

The way you then manipulate elements on your HTML document is by writing functions that take those data as arguments and change some kind of attribute of the selected element. 

#Showing things to scale

One of the other important D3 concepts is scale. For example, if you wanted to draw a circle on your document representing the US GDP ($18.56 trillion), you wouldn't want a circle that has a diameter of 18.56 trillion pixels. D3's `.scale` method helps you scale your data to the size of the graphic that you want to create. We'll discuss this more when we build our example. 

# You don't need to reinvent the wheel

There are tons of resources for learning D3 and perusing through code blocks created by other people.

## Online learning resources
  * [D3 documentation](https://github.com/d3/d3/wiki/Tutorials)
  * [Aligned Left](http://alignedleft.com/tutorials/d3)
  * [Dashing D3](https://www.dashingd3js.com/) -- not all content on this site is free
  
## Example galleries
  * [Official D3 Gallery](https://github.com/d3/d3/wiki/Gallery)
  * https://bl.ocks.org/ 
  * http://christopheviau.com/d3list/gallery.html
  
## Fancy examples
  * http://www.facesoffracking.org/data-visualization/
  * http://www.koalastothemax.com/
  
