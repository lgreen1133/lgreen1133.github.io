---
layout: post
title: Open Todo API
feature-img: "img/Todo_Feature.jpg"
thumbnail-path: "https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/Todo_feature.png"
short-description: An externally usable API for a basic todo list application.

---
Open Todo API was the second project in which I built a server-side API. After discussing with my mentor, we decided to build the front-end as well. 

### What can a user do?

A user can be authenticated via http basic auth (for API authentication). However, upon building the front-end, I used the devise gem to allow users to register and sign in directly via the app. 

In this simple app, the user can create lists and items within those lists. They can also mark them as done. 

### How did we improve it?

The original goal was for the API to return formatted responses that users can read, and machines can generate and parse. In order to do so, we needed to convert Rails objects into JSON representation (serialize). 

The API serializes the following:

* Users
* Lists 
* Items

This was done by implementing [Active Model Serializers](https://github.com/rails-api/active_model_serializers). _*Note: I had to use version 0.9.2._

I also used AngularJS to allow users to add lists and items. The list is collapsible. 

### Results 

* Front-end User Authentication was done via [Devise](https://github.com/plataformatec/devise)
* [Pundit](https://github.com/elabs/pundit) was implemented for authorization
* [AngularJS](https://angularjs.org/) was implemented to allow a quick, real-time update of the lists and items 

#### Using Curl Commands

_Create User_

`$ curl -u username:password -d "user[username]=Sterling" -d "user[password]=Archer" http://localhost:3000/api/users/`

_Create List_

`$ curl -u username:password -d "list[name]=Things to do today" -d "list[permissions]=private" http://localhost:3000/api/users/1/lists`

_Create Item_

`$ curl -u username:password -d "item[name]=Dance if you want to" http://localhost:3000/api/lists/1/items`

### Screenshots 

![alt text][logo]

[logo]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/todo_collapsed.png "Todo API Screenshot 1"

![alt text][logo2]

[logo2]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/todo_expanded.png "Todo API Screenshot 2"

![alt text][logo3]

[logo3]: https://s3-us-west-2.amazonaws.com/lgreen-screenshots-bloc/todo_completed.png "Todo API Screenshot 3"
