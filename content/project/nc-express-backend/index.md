+++
title = "NC-Express - REST API"
date = 2021-08-01
description = "Express and PostrgreSQL REST API"
tags = ["Development"]
categories = ["Development"]
download_url = "https://github.com/thick-hollins/nc-express"
project_description = "DESC"
project_name = "NC-Express backend"
project_url = "https://github.com/thick-hollins/nc-express"
release_date = "2021-08-01"
version = "0.0"
+++
[NC-Express on Github](https://github.com/thick-hollins/nc-express)

The goal of this project was to build a back-end for a reddit-like 'news' site using PostgreSQL and Express. 

{{< figure src="nc-e.png">}}

## Testing

The main thing I learnt from this project is the importance of testing to backend development. Tests are not just an external check on a backend application, but really also part of its structure and documentation. Once many features already exist in an application, it would be extremely difficult to add any further code without having a clear indication of the effect it is having on what already exists. 

{{< figure src="Screenshot.png" class="img-sm">}}

Having studied them at Northcoders, I was able to use a mock function to test a utility which interacts with the database. The Jest matcher `toHaveBeenCalledWith` confirms that the mocked database object has been called with certain arguments passed to the utility function.

## Queries

I enjoyed the process of building SQL queries, and especially where it was possible to use [PG-Format](https://www.npmjs.com/package/pg-format) and string interpolation to embed logic into query strings.

```javascript
const article = await db
  .query(`
  UPDATE articles
    ${inc_votes? 'SET votes = votes + ' + f.literal(inc_votes): ''}
    ${body? 'SET body = ' + f.literal(body): ''}
    WHERE article_id = ${f.literal(article_id)}
    RETURNING *;
  ;`)
```
However, since using MongoDB and Mongoose in my [final project](/project/waypoint-final-group-project), this kind of dependence on string manipulation seems a bit cumbersome in comparison.

## Users and tokens

Part of the specification of this project was to allow creation of user accounts, but how exactly users should be allowed to interact with the API was not specified. I used [JSON Web Tokens](https://jwt.io/) as a way to add basic authentication to user interactions with the database. With JWTs, I was able to protect sensitive functions. For example, an article may only be deleted by its author or a user with admin privileges. I used [Superagent Defaults](https://www.npmjs.com/package/superagent-defaults) to provide login credentials to a test user.

When it came to adding logout functionality, I ran up against a limitation of JWTs: there is no way to directly invalidate a token. A token may have a built-in expiry time, but nothing in the token itself can tell the server that the user to whom it was issued has logged out (or been logged out) before this time. [Reading up on the issue](http://cryto.net/~joepie91/blog/2016/06/19/stop-using-jwt-for-sessions-part-2-why-your-solution-doesnt-work/), I started to doubt that JWTs were a suitable way to handle user sessions.

{{< figure src="jwt-flowchart.png">}}

The need to revoke tokens meant that I had to store a list of 'logged out users'. I choose to use the minimal 'key-value database' Redis for this purpose, so as not to fill up the (supposedly RESTful) main database with stateful session data.

{{< figure src="redis.png" class="img-sm">}}

The database entries are automatically deleted at the same time as token expiry, so in theory, it is quite a lightweight system.

This side of the project gave me an understanding of the difference between a REST API and a broader back-end project requiring seperate servers for content and authentication purposes, and likely requiring third-party services for the latter. 

## Further development

The hosted project on Heroku provides data for my [frontend project](https://nc-express.netlify.app/). Not all database functions are implemented on that website. When I was implementing likes in the frontend, I found I had to go back to the database and make some slight adjustments to things I had believed were complete. I expect that if I were to add more features, for example, an front-end admin dashboard, I may once again have to revise this project to make it fully functional. As important as unit tests are, it's difficult to adress every potential problem without directly interacting with the database.