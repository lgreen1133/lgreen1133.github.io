---
layout: post
title: Blocmetrics
feature-img: "img/Blocmetrics_Feature.jpg"
thumbnail-path: "https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/Blocmetrics2.png"
short-description: An analytics service to track events on websites.

---
Blocmetrics was the first project in which I built a server-side API. We incorporated Rails and JavaScript. 

### What can a user do?

A user can register an account directly with Blocmetrics. Upon becoming a registered user, they can: 

* Sign in and out of Blocmetrics
* Register an application with Blocmetrics for tracking 
* View events associated with registered applications 
* Use the JavaScript snippet to capture client-side events in the application 
* See graph of events for each registered application 

### How did we improve it?

The project was improved by allowing the user to also perform the following: 

* Register multiple applications
* See their registered applications after creating them
* Re-register an application
* Delete existing applications
* View an index of registered applications 

### Results

* User Authentication was handled using [Devise](https://github.com/plataformatec/devise)
* [SendGrid](https://sendgrid.com/) was used to email users and have them confirm their accounts
* In the view of registered applications, I wanted to make the name of the application clickable. This improves the user experience giving them the option to visit the application via its link. Originally, I had written the code like so:

```
URL: <%= link_to @registered_application.url, "https://" + @registered_application.url %>
```

This was rerouting some URLs to the wrong location. I changed it to:

```
URL: <%= link_to @registered_application.url, @registered_application.url %>
```

* An API controller and routes were added to be able to receive incoming events from registered applications 
* CORS response headers were set to allow `POST` requests across domains
* [Chartkick library](https://github.com/ankane/chartkick#installation) and [Groupdate](https://github.com/ankane/groupdate) were incorporated to display pie and line charts for the events
* A [Bootswatch](https://bootswatch.com/) theme was applied 

### Screenshots 

![alt text][logo]

[logo]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/Blocmetrics1.png "Blocmetrics Screenshot 1"

![alt text][logo2]

[logo2]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/Blocmetrics2.png "Blocmetrics Screenshot 2"

![alt text][logo3]

[logo3]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/Blocmetrics3.png "Blocmetrics Screenshot 3"

[Link to Project](https://liz11-blocmetrics.herokuapp.com)