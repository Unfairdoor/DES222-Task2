# **Des222 Task 2 & 3 - Journal**
## a responsive design for the real world
### Gareth Cheetham

### An Overview
My initial project idea was to explore the use of Rest API's and web development, wanting to expand on my coding portfolio after struggling with my Task 1 implementation.  
After exploring some public API's I discovered that NASA have public API's for a whole heap of different API's that you can explore and utilise. I knew immediately this could be interesting, the hardest part would be choosing a topic from their list that I could make someone else interested in aswell.

![List Of NASA's APIs](/Images/NASA%20Api's.png)

The following is a Process Documentation outlining how I'm building my Project.

### The Idea

The Mars Rovers have always facinated me. They're the modern version of astronauts, a millenial's explorer, and following their exploits scratches that itch of exploring the unknown. I feel that the Rovers all having names gives them their own personality and they become a certain kind of character, like the previous generation's Buzz Aldrin or Neil Armstrong. They can be someone you root for, showing an uncanny ability of humans able to project their traits on inanimate objects.

Currently on the surface of Mars, NASA has 4 rovers: Curiosity, Spirit, Opportunity and Perseverance. Each rover is in a different area and are each surveying the land and taking samples as well as an unbelievably large number of pictures. There are many ways NASA has developed to follow their journeys:

#### Multiple Cameras

![List of Rovers and their cameras](/Images/Rover%20Cams.png)

#### Interactive Map

![Interactive Rover Map](/Images/Rover%20Map.png)

Link: https://science.nasa.gov/mission/mars-2020-perseverance/location-map/ 

#### Access Mars
This is a neat project that is a rudimentary 360 experience that has stitched together images taken from Curiosity's landing zone that has a voice over that explains some interesting features of the Curiosity rover as well as a short animation explaining the Curiosity launch mission.

Visit: https://accessmars.withgoogle.com/ to have a look!

![Screenshot of NASA's Access Mars Web app](/Images/Access%20Mars.png)

I'm spoiled for choice, there's a great documentation for queries using the Mars API, maintained by [Chris Cerami](https://github.com/corincerami/mars-photo-api), so I have a lot of faith that whatever I choose to do, I have the necessary tools to help me figure out how to execute it.
Speaking of whatever I choose to do, what do I have planned?

The idea is to have a site that will have the most recent pictures of each rover and each camera on display. Though at this point I'm not 100% sure how often the API is updated with new pictures, I believe that it would be possible to create a script that would update every time the page is reloaded. The intention is not to serve as a database like NASA already has implemented, but instead to serve as a 'What's New?' style of catalogue, not storing any pictures at all.


#### The Last 2

Of the 4 aforementioned NASA rovers, only two remain. 
In May 2009, Spirit became stuck in soft soil at a site called "Troy". After months of testing and manoeuvres, NASA ended their efforts to free the rover and ended its mission on May 25th 2011. Spirit's journey began in 2003 on a 90 day mission to explore signs of water and far exceeded its expected operation time.![Read More Here](https://www.jpl.nasa.gov/missions/mars-exploration-rover-spirit-mer-spirit/)

Opportunity was Spirit's twin rover, landing on Mars in 2004, it made a number of discoveries in its 90 day mission, then continued operations until June 2018, exceeding its life expectancy by 60 times. It stopped communications after a severe Mars-wide dust storm blanketed the rover's location, after a failed attempt to revive the rover in February 2019, efforts were ceased, and the rover's status is now past.

Curiosity and Perseverance are currently still active on the Mars surface, below is a diagram NASA has provided the public outlining the locations of all Curiosity's cameras.

![Curiosity Camera Locations](/Images/Curiosity%20Camera%20Locations.png)


### Site Layout

I have no strong direction I want to take the site, so I'm going to wing the design and play around with elements until something clicks. The colour scheme I can't make up my mind if I'd prefer something that is Mars-themed (lots of warm tones, reds, maroons, etc.) or something more generically space-ey like wistful cool blues and purples. Another great theme to take inspiration from could be NASA's own ![site](https://www.nasa.gov/).

![NASA Site Example Clip](/Images/NASA%20Site%20Example.png)

#### What's in it?

So the main idea is to have the most recent pictures the rover has taken. The main problem is, there are a lot of cameras on each rover. Some are used MUCH more often than others as they all serve different purposes. Some are used for navigation, some for hazzard identification and the curiosity even has a camera called CHEMCAM which sends a high-powered lazer to vaporize an object then take an infre-red picture to help identify the object's chemical composition.

With so many cameras, simply throwing them all up onto a dashboard I think would be too confusing, so I'd like to have some sort of selection system. Initially I had thought of having some sort of interactive object that would highlight cameras as you moused-over them and you click to bring up the associated pictures. After seeing the arrangement, particularly of each rover's mast having 3 different types of cameras in a small area, that idea seemed a bit clunky. I think a tabular-based system would work well, but to keep the idea of highlighting I decided to find an image that clearly shows all cameras and just colour the corresponding camera and display it on each tab.
Turns out that NASA has 3D models of each rover in the public domain, so I can download them and edit the UV Textures accordingly!

![Curiosity 3D Mesh](/Images/Rover%20Mesh.png)

![Curiosity ChemCam Highlight](/Images/Mast%20Camera%20Highlight.png)

### Figma Layout

![Figma Screenshot 1](/Images/Figma%20Screenshot%201.png)

Here is my first mockup of a site layout in figma. The design uses somponents of a manilla folder to seperate the different cameras of each Rover. I have the rover selection at the bottom, but I could just as easily see them being situated at the top of the screen too.
The background is a simple black and the colour scheme is following a warm colour palette to simulate Mars.

I'm not yet sold on it and I'm going to try more variations.

### Exploring the API

The API has some brilliant documentation and has some simple lookup queries to get images from the rovers. After looking through the queries, I have the found the formatting can be layed out as the following:

API requests use the following format
Base URL
https://mars-photos.herokuapp.com/api/v1/rovers/{ROVERNAME}/photos?{QUERY}&{HERE}
You can also substitute the '/photos?' for '/latest_photos?' For the most recent sol for which photos exist
Queries are seperated by & and can be in the following order:
?sol={SOLNUMBER}&earth_date={yyyy-mm-dd}&camera={CAMERA}

When the requests are sent, they return a JSON with the requested information, which can be a little long-winded but it has everything we need, here is an example code snippet.

![GET Request](/Images/GET%20Request.png)

From here we can extract just the image link:

![Image Link](/Images/Filtering%20for%20Image.png)

Which returns this:

![FHAZ Extraction example](/Images/FHAZ%20Example.jpg)

Next is to implement this code or a version of it into HTML and Java for a desktop version. 

#### Possible Additions:

- **Notifications:** A notification system could be interesting to implement, not so much as doing push notifications to an app or anything, more like a little 'NEW' sticker above the tabs that have updates the same day the the webpage is accessed.
- **3d Models:** There could be some way to implement a viewer for 3d models on the site. I have no idea how difficult that would be, however
- **Rover Locations:** Similar to the 3d models, it could be interesting to integrate NASA's interactive maps into the site. It doesn't really relate to the 'responsive design' aspect of the bried though.
- **Current Orbits:** Having some way to show Mars's orbit compared to Earth's at the time of the picture would be interesting too, though while the 3d models and maps are provided by NASA, I can't find any good orbit models available so this may be less feasable than the others.


# ----TASK 3 STARTS HERE----

## Site Progress:

I used a tool called DhiWise to convert the Figma file to a HTML code base. The site worked okay, they don't allow you to copy or download code without paying them $150 for an annual subscription, so I just manually copied the code base.
It worked fine, but there was a lot of pieces of the site that just don't work correctly, so a lot of editing was required to get the code to a workable state.
Their naming conventions were interesting, I may end up changing it later to help it make more sense in the context of this project, but as it stands right now I'm leaving everything ver-batem just so the CSS works correctly.

![DhiWise Logo](/Images/dhiwise%20logo.jpeg)
![DhiWise Code Snippet](/Images/Dhiwise%20Code%20snippet.png)

With some editing, this is what the site currently looks like. I'm now working on implementing lookup functionality, which involves converting the python script to Java and implementing that in to the strange HTML that DhiWise made.
I'm still not sure if it was worth using this tool, the amount of time I've spent trying to figure out what they produced may not have been spent well.
![Site Progress](/Images/Site%20Progress.png)

Due to me not knowing a lick of Java script, I relied on chatGPT to help make the Java scripting version of my python code.
This snippet returns the most recent image taken by the rover, now what's left is to customise the image query to correspond to the correct rover and camera and we're looking great.
![Javascript Snippet 1](/Images/Javascript%20lookup.png) 

Here is the updated function that now takes arguments to change the API query dynamically
![Javascript Dynamic Lookup](/Images/Javascript%20Dynamic%20lookup.png)

This approach was a bit clunky as it's sending an API request every time a button is pressed. To combat this, we will pre-load all of the API requests, storing the URL to each image so we can swap seamlessly between camera images.
To do this, we simply put the 'getImageURL' function into a foreach loop that initialises for each camera when the page is loaded, updating the IMG URL field in each camera's information in the publically stored array.
![Pre-load image URL lookup](/Images/Pre-load%20image%20Links.png)

With this, the site has the baseline functionality for the first rover. There are still things to be done like adding in the elements I need to be changed, such as each camera description and the different images of each highlighted camera, however the actual functionality works.
The next big milestone is to implement Perseverance into the mix as well. This is going to involve adding in the functionality of the switching buttons at the bottom of the screen. This is going to require retooling of the current scripts so I am imagining it to be quite an endeavor.

### Milestone 2 - Switching Rovers

As I discussed in the previous section. To change rovers is going to require retooling of how the script approaches storing information, as well as figuring out how to dynamically change the buttons to switch cameras. 
I'm really not sure how I am going to change how the buttone line up either, but I'm pretty sure that it'll be required to be addressed as Perseverance has significantly more cameras than Curiosity. Also on that note,
Curiosity's cameras seem to either be out of commission or they're having a significant delay in use. Of the 7 cameras, 3 have not been used recently enough to work with the recent_images API lookup, these are the MAST Cam, CHEMCAM and MARDI. 
I don't know how to see the most recent image each of these cameras have taken without using the latest_image API request.
An idea I had was to sun a for loop that will just check each SOL until it returns an error then tell me the last recorded SOL, problem is I don't know if the API will allow that many lookups, as it would be significant.
I may just end up having a stock image saying 'NO NEW IMAGES'. I won't remove the tabs for these cameras as I can still give information about the camera, what they do and where it is on Curiosity.
Anyway, back to the task at hand.

First we need to expand the list of cameras:
![Expanded camera dictionary](/Images/Camera%20Dictionary.png)

Next we add a function to clear the tabs in the html and then reinstantiate them with the new data from the camera dictionary depending on which dictionary is loaded.
![Dynamic Tab updating](/Images/Dynamic%20Tab%20updating.png)
![Rover Button update](/Images/Rover%20Buttons%20Updated.png)

We now need to expand the cameraData to hold the information we are going to be displaying. The initial idea was to use a JSON format, it turns out that you can't do that without hosting a server to load the JSON in to first for security reasons.
Not wanting to mess around with any of that stuff so the assessment submission is as smooth as possible, I'm going to just hard-code the data structure into the Java file. It isn't too long it just looks a little messy.

![JSON Networking Error](/Images/JSON%20Networking%20Error.png)
![JSON Fetch Function](/Images/JSON%20Fetch.png)
![JSON coded into Java](/Images/JSON%20coded%20into%20Java.png)

While it wasn't pretty, it worked, the real problems came when trying to swap rovers.

### net::ERR_INTERNET_DISCONNECTED

After re-tooling the codebase to swap between rovers, I started running into problems with the basic functionality of the code.

TLDR: Google chrome stopped liking the API so now I can only use Edge.

I honestly have no clue what is causing this issue, but when it came to any queries utilising the API, google chrome throws an error suggeting that the tab has no access to the internet.
Initially I thought it had something to do with the rate of queries being sent to the API, so I stopped the pre-loading function and went back to only loading images when each camera is loaded.
The code will call the API on button click and then store the link it fetched, as well as adding the cameraName to a small list of cameras it has already pre-loaded.
I have kept this solution in the current code base with no intentions of changing it back, but safe to say, it wasn't the API. 
chatGPT suggested it may have something to do with CORS headers which from what I gathered is something to do with permissions from packets sent to sites, but honestly I really didn't understand it fully.
I also looked at some suggestions on Stackoverflow, who also just suggested that the tab is offline, so I tried pushing my site to GitHub so I can host it on pages, hoping that if I wasn't querying an API locally then it would help solve the problem.

![The bane of my existance.](/Images/ERR_INTERNET_DISCONNECTED.png)

It did not.

So, after further troubleshooting, checking API limits, implementing code snippets that semmed to do nothing, even routing through a proxy site that bypasses supposed CORS issues.
I then tried using Edge as the browser.

It worked.

I am only using edge from here on in and I am going to have to ask you to boot the site on Edge...

What has the world come to.



I spent too much time on this.


## Goodbye 'latest_photos'

It has been a while since my last update with some frustrating realisations that needed to be fixed.
We last left off trying to solve CORS issues caused by Google Chrome's security measures. Since then I have discovered that the 'latest_photos' query for the API really doesn't work well at all. Many of the cameras simply aren't updating this query and I have no idea why. I do know however that this issue lays with the API and not on my end, so it is not something I can fix. While diving into the source code of the lookup API, I found a way that NASA is tracking which sol their Mars Rover missions are up to, and it is done through [THIS](https://mars.nasa.gov/rss/api/?feed=raw_images&category=mars2020&feedtype=json&latest=true) link, which is essentially just a JSON of the latest sol and the number of images taken. Regardless, this means I am able to keep up with the latest sol without having to do any fancy date conversions using the computer's clock, consequently I can change the way we are looking up the images taken by the rovers so I'm not relying on the awful and not at all maintained 'latest_photos' lookup I was using.

#### What does this mean?

So the new lookup format is the following::

https://mars-photos.herokuapp.com/api/v1/rovers/${roverName}/photos?camera=${cameraName}&sol=${latestSol}

So we have removed the 'latest_photos?' query and replaced it with simply 'photos?'. We also have added the lookup to check a specific sol using '&sol=${latestSol}'.
The wonderful thing is that this works for both rovers and has significantly reduced the number of cameras that have no image source!
Here are some snippets of the new code:

![Fetch Latest Sol](/Images/Fetch%20current%20Sol.png)

The sol needs to be reduced by 1 so all the images are a day old, just to compensate for upload times. The async function was needed so that the sol was fetched more reliably, as it was sometimes being skipped. A pause was also needed to be added to the 'swap rover' function due to this lookup too, it seems to take quite a long time to get this information and I don't really know how to fix that.

![Wait for sol fetch](/Images/Wait%20for%20latest%20sol.png)

This has now been expanded upon, using an overlay 'loading screen' that blocks user input so that another is queued up while awaiting the API response. This is done by awaiting the fetchLatestSol function to finish before removing the loading screen. ---This functionality has since been removed due to formatting issues with the style sheet. I would have loved for it to be implemented, but I ran out of time to solve its issues---

### The Final Update

Due to my poor planning skills I have run out of time to implement everything I'd have liked to. Granted, the scope for the project kept increasing as I worked on it and found functionalities that I wanted to improve.
The final implementation far exceeds my first attempt at a site design in Task 1, which is mainly what I set out to accomplish. I understand a little bit better how HTML layouts and CSS work together, although I still feel that I could spend eternity on CSS and I still wouldn't feel confident.
I also have had more exposure than I expected to Javascript coding and, while I wouldn't consider myself remotely competant at it, I at least can recognise a good portion of what it is doing.


The large majority of the work that has been put in to the project towards the end was grunt work. Labelling things correctly, sorting file locations, sourcing images from the 3d models, etc.
It's work that while it isn't difficult, it turned out to be extremely time consuming. That and trying to figure out what CSS is doing to my website layout.


## In Conclusion

I'd like to think this excercise as a success, and even though I underestimated the scope of my proposal, I am happy with the work that I managed to complete.

Some things to improve:
    - **API Load Times** - The api load times are extremely inconsistant. If you're finding that the site isn't loading something properly, try reloading and clicking only 1 thing at a time.
    I PROMISE IT WORKS!!! I mentioned in an earlier section that I had a load-screen implemented at one point. I unfortunately had issues with it when I was messing with the final CSS layouts and styles and had to cut it which is a shame because now you can overload the site while its looking things up and forgot to take a screenshot.
    - **Button functionalities** - This is only a visual issue, but I would have liked the buttons to stay highlighted so you know what combination of rover/camera you're viewing. REight now it deselects as soon as you click something else which is annoying. The way to fix this is by changing the button styles within the javascript, not in the style sheet, I just ran out of time to implement it.
    - **Curiosity's SOL API** - I only figured this out at the end, but the API that is used on the page initialisation is actually only keeping track of Perseverance's mission. So Curiosity, who is significantly older, only shows their photos from about 8 years ago (WHOOPS!).
    Again, I ran out of time to find another API that is keeping track of Curiosity's mission's Sols (If it even exists). I wish the latest_photo api actually worked properly so I didn't have to use it, the perseverance sol tracking API already slows down the site's load time significantly.
    


![University of the Sunshine Coast Logo](/Images/USC%20logo.PNG)
