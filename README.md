###FEND P4: Website Performance Optimization - Final Project
Student: Keith Thomson

#### Where to find it

Source code can be found in this github repository in branch "gh-pages":
https://github.com/jkt2407/frontend-nanodegree-mobile-portfolio

Website can be accessed through Github pages:
http://jkt2407.github.io/frontend-nanodegree-mobile-portfolio/

#### Final Project Notes

#### 1. Critical Rendering Path for index.html
Optimizations:
- Reduced the size of img/prfilepic.jpg and view/images/pizzeria.jpg
- Removed the Google font "Open Sans" and used Arial instead
- Put some styles from css/style.css (the styles that are used by index.html) in line in header section and loaded the whole file css/style.css later, asynchronously
- Removed Google Analytics JavaScript
- Added a media query to the link to css/print.css so it won't block rendering for screen

To see these changes, search for "optimization:" in index.html.

Results: PageSpeed scores for
	http://jkt2407.github.io/frontend-nanodegree-mobile-portfolio/index.html
- Mobile: 95/100
- Desktop: 97/100

#### 2. Framerate for pizza.html
Optimizations:
- In views/js/main.js,
 - Limited the number of rows and columns of pizzas created -- just create as many as fit on screen
 - Kept an array of pizzas so we can access them quickly rather than having to traverse the DOM looking for them
 - In updatePositions(), made computation of "phase" a table lookup rather than recomputing it every time

To see these changes, search for "optimization:" in views/js/main.js.

Results:

- Timeline display in DevTools shows consistent frame times at 60 fps or better
- Console output shows times under 0.2
 - main.js:500 Average time to generate last 10 frames: 0.17999999999992725ms
 - main.js:500 Average time to generate last 10 frames: 0.19650000000001455ms
 - main.js:500 Average time to generate last 10 frames: 0.18349999999991268ms
 - main.js:500 Average time to generate last 10 frames: 0.17950000000000726ms
 - main.js:500 Average time to generate last 10 frames: 0.21099999999996727ms
 - main.js:500 Average time to generate last 10 frames: 0.19399999999995998ms
 - main.js:500 Average time to generate last 10 frames: 0.1964999999999236ms
 - main.js:500 Average time to generate last 10 frames: 0.18350000000018554ms
 - main.js:500 Average time to generate last 10 frames: 0.18299999999981081ms
 - main.js:500 Average time to generate last 10 frames: 0.17150000000001456ms

#### 3. Computation Efficiency for pizza.html
Optimizations:
- In views/js/main.js, changePizzaSizes()
 - removed document.querySelectorAll() from "for" loop
 - removed computation of new width from "for" loop since all pizzas will be the same width

Results:

- Time to resize pizzas is about 1.3 seconds, as reported by console

 ***

For reference, here are the original contents of the readme file:

## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

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
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js.

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

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

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
