+++
title = "Waypoint 🚶 group project "
date = 2021-09-24
description = ""
tags = ["Development"]
categories = ["Development", ""]
download_url = "https://github.com/thick-hollins/waypoint-be"
project_description = "DESC"
project_name = "Waypoint"
project_url = "https://github.com/thick-hollins/waypoint-be"
release_date = "2021-09-24"
version = "0.0"

+++
{{< youtube rmPnrpoBBiA >}}

[Back-end code](https://github.com/thick-hollins/waypoint-be)

[Front-end code](https://github.com/thick-hollins/waypoint-fe)

For our final project at Northcoders we had two and a half weeks to plan and build a project of our choice, showing off our back-end and front-end development skills, in a group of five.


My group's choice was **Waypoint**, an app to allow users to record their walks, along with points of interest along the way, and to share them on a social network. We summed this up as a 'social tour-guide app'. The tours could be anything from a rural hike, to a historical city-walk or even a pub-crawl.

{{< figure src="welcome.png" class="img-lg">}}

### Spiking

To ensure that our project was viable within the given time-frame, we started our work by exploring the possibilities for recording GPS on a mobile device. Our first success in this regard was using [Expo Location](https://docs.expo.dev/versions/latest/sdk/location/) and the relative ease of using that package across our team's differing development environments meant that we quickly settled on it, and therefore, on **React Native** as our front-end framework. 

### Road-testing

Although we had a minimal proof-of-concept in terms of accessing out phones' location services, it took further work to get to the point of building a full route while the device was left in the user's pocket. With this eventually in place, we split off into front-end and back-end teams.

### Data

We had decided to use **MongoDB** as our database, to explore alternatives to SQL. After some work to familiarise ourselves with building a database scheme in that environment, out task was to generate and seed test-data which could then serve as a basis for front-end development. Our project didn't use any external API as a data-source, so we had to generate everything necessary to simulate a social network with follows, likes, posts, images and lists of valid co-ordinates (our routes). 

{{< figure src="1.jpg" class="img-lg">}}

### Visuals

The work on the front-end began with rendering sequences of co-ordinates as lines and points on a map using React Native Maps. This became the basis for a 'post' view and a 'feed' view. 

### Photos

Expo once again provided us with a handy API for accessing our phones' cameras and camera-rolls, and for cropping and re-sizing images. We requested a pre-signed URL from **Amazon S3**, and sent our photos directly to their servers, and stored the photos' locations in our database.

{{< figure src="2.jpg" class="img-lg">}}

### React Native

Although we were all already familiar with React, there were challanges in adapting to a different style of navigation on mobile devices. In-built componenents were also significantly different to those we were familar with. We found the extensive documentation on this platform very helpful.

### Back-end technologies

**Mongoose** provided an extremely convenient wrapper for MongoDB in Javascript, and allowed us to quickly adapt our database models as new requirements for the project emerged. **Express** was also a good choice in this regard, because we were already familiar with it, we were able get our server up and running quickly.

### The final product

On the last day of development, we left our computers and went out to record our own tours and waypoints. We created our own user accounts and posted our own routes, photos and comments.

### Further development

We had initially intended that users would be able to click 'follow route' on their friends' posts and then see their own location overlaid on the recorded route, so as to be able to go on a tour, and view their friends photos and comments on the places along the way. We didn't have time to implement this feature, but it would certainly be the next step if we were to continue development.

We would also like to issue notifications when a user approaches their friend's waypoint, as they follow a route. Geo-fencing could provide a good basis for this feature.

Personally, I would like to get to know MongoDB more deeply and explore the possibilities of non-relational databases. For example, could we have designed our database more efficiently by embedding certain documents within others?

{{< figure src="S24.png" class="img-lg">}}

