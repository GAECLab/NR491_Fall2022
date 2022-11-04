# Mapping with Leaflet

---

**Objectives:**

By the end of this exericse, you should be able to:

* Create an HTML page
* Host an interactive map (Leaflet) on GitHub Pages

---

In this exercise, you will learn how to build a Leaflet map and host a live version of an HTML webpage on GitHub Pages.

**Leaflet** is an open-source code library for creating interactive maps based on three core coding languages: HTML, CSS (Cascading Style Sheets), and JavaScript. We will mostly be interacting with the HTML file for our map.

**HTML** (HyperText Markup Language) is a markup language used for files meant to be displayed in a web browser. HTML syntax is similar to the `markdown` syntax used in these `jupyter notebooks`. From [Wikipedia](https://en.wikipedia.org/wiki/HTML):

"HTML elements are the building blocks of HTML pages. With HTML constructs, images and other objects such as interactive forms may be embedded into the rendered page. HTML provides a means to create structured documents by denoting structural semantics for text such as headings, paragraphs, lists, links, quotes and other items. HTML elements are delineated by tags, written using angle brackets. Tags such as `<img />` and `<input />` directly introduce content into the page. Other tags such as `<p>` surround and provide information about document text and may include other tags as sub-elements. Browsers do not display the HTML tags but use them to interpret the content of the page."

This exercise and code is adapted from the section [Copy, Edit, and Host a Simple Leaflet Map Template](https://handsondataviz.org/copy-leaflet.html) from the *Hands-On Data Visualization* book by Jack Dougherty & Ilya Ilyankou. The open-acess web edition of the book can be found [here](https://handsondataviz.org/).
First, go to the GitHub repo: https://github.com/HandsOnDataViz/leaflet-map-simple

Then, click the green `Use this template` button to copy this repo to your GitHub. *Note:* This is not how accessing other people's repositories usually works. This repo is set up to work as a tutorial, so you can use the template multiple times if you wanted.

Name your repo `leaflet-map-simple` and click the green `Create repository from template` button.

Hooray! You now have (at least) 2 repos on your GitHub!

Next, try getting this repo onto your local computer. 

---
Navigate to the folder on your local computer. It should be names `leaflet-map-simple`. Double click on the `index.html` file. What happens?

Open the **folder** in VS Code and open the `index.html` file.

### A Brief Intro to HTML and Leaflet Markers

Now that we have the HTML file open, let's expore what it means. There are several comments in the document to help our understanding of the document.

"The first block tells web browsers which formatting to apply to the rest of the page of code. The second block instructs the browser to load the Leaflet code library, the open-source software that constructs the interactive map. The third block describes where the map and title should be positioned on the screen. The good news is that you don’t need to touch any of those blocks of code, so leave them as-is. But you do want to modify a few lines further below." [(Ch. 10, Dougherty & Ilyankou, 2022)](https://handsondataviz.org/copy-leaflet.html)

Once we are in the `<body>` section of the HTML document, we are looking at code that can be used to edit our map. You can easily change the code where you see `EDIT` in a comment. 

Take some time to explore changing the `map-title`, the center coordinates, and zoom of the map. After you make a change, save the file and refresh your browser with the map. Are your changes appearing?

---

#### Setting the map to Raleigh

Change the initial map center coordinates to Raleigh (look up the coordinates on Google).

Next, let's edit our marker to NC State's main campus and give our marker a useful pop-up. Edit the coordinates to `35.7847` and `-78.6821`, and change the pop-up text to `NC State University`.

Save your `index.html` file and refresh your web browser. What happened?

To add another marker, just add another leaflet marker by copy and pasting the `L.marker(...)` code. Here's an example for Jordan Hall:

```
  /* Display a point marker with pop-up text */
  L.marker([35.7818, -78.6763]).addTo(map) // EDIT marker coordinates
  .bindPopup("Jordan Hall"); // EDIT pop-up text message
```

Take a few minutes to add 2-3 markers around Raleigh, with descriptive names. This is also a good time to add *this* file to your `leaflet-map-simple` folder. It has some handy instructions that would be nice to keep together with your map code in your repository.

When you're done, go through our **git** workflow to put these changes on your *remote repository* with a helpful commit message.

---
### Hosting your map with GitHub Pages

Try clicking on your `index.html` file in GitHub. It opens the code, but where is the map? This is where GitHub Pages comes in!

**GitHub Pages** is a built-in feature of GitHub that allows you to host a live, online version (i.e., webpage) of your HTML file that anyone can view on their browser. 

*Note:* "there are some restrictions on usage, file size, and content and it is not intended for running an online business or commercial transactions." [(Ch. 10, Dougherty & Ilyankou, 2022)](https://handsondataviz.org/copy-leaflet.html)

#### Getting GitHub Pages set up

From your `leaflet-map-simple` repo, click the `Settings` button at the top right.

On the menu on the left-hand side, find the `Pages` option under `Code and automation`, and click on it. 

Next, make sure your the drop-down menu for `Source` under `Build and deployment` has `Deploy from a branch` selected. Then, under `Branch`, change the drop-down menu from `None` to `main` (leave `/(root)` as is) and click `Save`. Now GitHub will publish a live version of your map to the internet!

GitHub should refresh to show the online address for your map. Open the link in a new tab. This is your GitHub Pages **live website!**

Next, let's update our README to have our individual map website links in place of the handsondataviz website. 

**Try changing the README either on GitHub or in your local repo, and then get your local and remote repos to match using what we learned in the github_intro exercise.**

---
### Additional edits for Leaflet

We can edit the basemap tile layer that is our map background by going to the `L.tileLayer()` code block.

"Our template uses a light map with all labels, publicly provided by CARTO, with credit to OpenStreetMap. One simple edit is to change `light_all` to `dark_all`, which will substitute a different CARTO basemap with inverted coloring. Or [preview several other Leaflet basemap code options](https://leaflet-extras.github.io/leaflet-providers/preview/) that you can copy and paste. Make sure to attribute the source, and also keep `}).addTo(map);` at the end of this code block, which displays the basemap. 

... 

Warning: Be careful when editing your code. Accidentally removing or adding extra punctuation (such as quotation marks, commas, or semicolons) can stop your map from working. But breaking your code—and fixing it—can also be a great way to learn." [(Ch. 10, Dougherty & Ilyankou, 2022)](https://handsondataviz.org/copy-leaflet.html)

Always be sure to save and commit your code and refresh your browser to see the changes to your map/website. If you don't refresh it can take 30 seconds or longer for GitHub Pages to process your newly commited code.

### Congrats! You now have a live map webpage!!

On to storymaps!
