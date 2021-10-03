+++
title = "NC-Express 📰 the website"
date = 2021-08-20
description = ""
tags = ["Development"]
categories = ["Development", ""]
download_url = "http://github.com/USERNAME/PROJECTNAME"
project_description = "DESC"
project_name = "PROJECTNAME"
project_url = "URL"
release_date = "DATE"
version = "0.0"

+++
[Hosted project](https://nc-express.netlify.app/)

[Code](https://github.com/thick-hollins/nc-express-site)

My front-end project at [Northcoders](https://northcoders.com/) was a chance to make a React app consuming my own [NC-Express API]({{< ref "/project/nc-express-backend" >}}). The site allows you to:

- Browse articles on the home page, sort by date or likes
- Browse articles by topic
- Comment on articles
- Post articles
- Edit your own articles and comments
- Up and down-vote others' articles and comments
- Create topics
- Browse users and see their authored articles and liked articles
- Edit your own profile

### Responsiveness

The site uses a simple single-column layout which is narrow enough for mobile devices, but which expands to a wider view on larger sceens. I designed the site with a narrow viewport in mind, and no media queries were necessary to adjust it dynamically.

{{< figure src="Screenshot_2.jpg" class="img-lg">}}
{{< figure src="Screenshot31.png" class="img-lg">}}


### Navigation

Routing is handled with React Router and although the site is a single-page-app, URLs are available to the user. A NavLink component in the page header gives a visual indication of the active site-section.

### Votes

A user's votes are fetched on login and then stored in a global context. The Vote component has access to this context, and updates it optimistically as well as sending vote data to the API. Votes are validated in terms of uniqueness both within the front-end and back-end. Optimistic rendering is also used to ensure speedy feedback when posting articles and comments.

### Further Development

The API's login, logout and signup functionality are not yet implemented on the front-end - instead a default user's credentials are hard-coded. I would like to add the necessary pages to the site to allow these functions to be used. I would store credentials obtained from the API in Local Storage, so they could persist between site-views. An admin dashboard would also be required for a site-admin to access protected routes, for example to delete another user or their content. 

In its current form, the site's styling is contained in a single CSS file. I would like to implement a CSS-in-JS alternative here such as Styled Components.