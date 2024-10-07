# **Des222 Task 2 - Journal**
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

With so many cameras, simply throwing them all up onto a dashboard I think would be too confusing, so I'd like to have some sort of selection system. Initially I had thought of having some sort of interactive object that would highlight cameras as you moused-over them and you click to bring up the associated pictures. After seeing the arrangement, particularly of each rover's mast having 3 different types of cameras in a small area, that idea seemed a bit clunky. I think a tabular-based system would work well, but to keep the idea of highlighting I decided to find an image that clearly shows all cameras and just colour the corresponding camera and display it on each tab. Turns out that NASA has 3D models of each rover in the public domain, so I can download them and edit the UV Textures accordingly!

![Curiosity 3D Mesh](/Images/Rover%20Mesh.png)

![Curiosity ChemCam Highlight](/Images/Mast%20Camera%20Highlight.png)

### Figma Layout

![Figma Screenshot 1](/Images/Figma%20Screenshot%201.png)

Here is my first mockup of a site layout in figma. The design uses somponents of a manilla folder to seperate the different cameras of each Rover. I have the rover selection at the bottom, but I could just as easily see them being situated at the top of the screen too.
The background is a simple black and the colour scheme is following a warm colour palette to simulate Mars. I'm not sold on it personally and I'm going to try more variations.

### Exploring the API

The API has some brilliant documentation and has some simple lookup queries to get images from the rovers. After looking through the queries, I have the found the formatting can be layed out as the following:

API requests use the following format
Base URL
https://mars-photos.herokuapp.com/api/v1/rovers/{ROVERNAME}/photos?{QUERY}&{HERE}
You can also substitute the '/photos?' for '/latest_photos?' For the most recent sol for which photos exist
Queries are seperated by & and can be in the following order
?sol={SOLNUMBER}&earth_date={yyyy-mm-dd}&camera={CAMERA}

When the requests are sent, they return a JSON with the requested information, which can be a little long-winded but it has everything we need
![GET Request](/Images/GET%20Request.png)

This returns 

![University of the Sunshine Coast Logo](/Images/USC%20logo.PNG)
