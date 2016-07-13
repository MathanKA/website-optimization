## Website Performance Optimization portfolio project
=====================================================

1. I have created thumbnail image of pizzeria.jpg for portfolio page and reduce size of pizzeria.jpg for pizza page.
2. I have added 'will-change: transform' attribute to background pizzas class (mover) for smooth movement.
3. In main.js I have moved mover class selector out of the loop in updatePositions to remove forced synchronous layouts.
4. In main.js I have removed determineDX function and replace it by function which resizes pizzas using % of original size.
5. Since calls to google servers to retrieve fonts may take a while (depend on internet connection) I have found solution to host myself font I need. Please refer to https://google-webfonts-helper.herokuapp.com/fonts
6. JavaSrcipt in index.html:
   - I have moved perfmatters.js to the end of the body so it wont block rendering
   - Also I have moved anonymous GoogleAnalytics function to the end of document
   - But I have just added 'async' attribute to the http://www.google-analytics.com/analytics.js
7. I have extracted basePizzasPositions out of the updatePositions() so I wont need to request movableItems[i].basicLeft attribute every time.
8. On loading main.js script after creation of pizzas, requests updatePossitions which calls document.body.scrollTop which forces layout. But on page load scroll will always be 0 so no need to request that value. Instead I have added argument to updatePossition which is the scroll position and extracted document.body.scrollTop to scroll event listener. This way I have only one layout phase.
9. I have reduced number of pizzas from to 200 to as many is actually is needed to cover the page height (please refer to variable viewPortHeight).
10. In intex.html I have added media 'print' for print.css so I wont load it when I am not printing.
11. In index.html I have embeded style.css to reduce number of requests.
12. I have reduced size of profilepic.jpg.
13. I have minimalized perfmaters.js

HOW TO RUN:

1. Open in chrome index.html :)


*********************************************************************************************

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

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
  $> ngrok http 8080
   ```
   
* Minify and inline "style.css"
* Minify and inline "perfmatters.js"
* Add "Async" attribute on all JS tags
* Add "print" media attribute on "print.css" link tag
* Move Google font link to the end of body tag
* Optimize and resize images
* Minify index.html


#### Part 2: Optimize Frames per Second in pizza.html

* Move document.querySelector("#movingPizzas1") out of for loop and replace querySelector with getElementById
* Replace querySelectorAll, querySelector with getElementsByClassById and getElementsByClassName and put them in a variables for reuse
* Change the calculation of newwidth using "WindowWidth * size ratio" to minimize usage of offsetWidth
* Append elements to DocumentFragment first then finish by adding that to the DOM
* Resize and optimize pizza picture and remove style.height and style.width change
* Use requestAnimationFrame on scroll event
* Cut down amount of background pizzas from 200 to 36
* Precaculate the five dx values and put them in phases array in order to move calculation out of For
* Optimized For loop with iterating in reverse order
* Optimizing Images, CSS and JS files
* Use innerHeight to determine how many pizzas to generate

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>
