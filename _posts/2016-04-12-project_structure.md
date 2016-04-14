---
author: Sergey P.
title: "Project's sources structure"
layout: post
description: "A few years ago discussions about the way of project's sources and files are organized were like religious wars in Java world. What is the matter?"
redirect_from: ["/2016/04/12/project_structure.html"]
image: "/img/holy-war-holy-shit.jpg"

---
![](/img/holy-war-holy-shit.jpg)

A few years ago discussions about the way of project's sources and files are organized
were like religious wars in _Java world_.

But what is the matter today? Because even in current _JavaScript era_ I think this topic is still actual and those practices can be applied to projects also based on the new technologies. So, below are my notes I made at mentioned time.    

The are two fundamental ways to structure project's packages: _Package-by-layer_ and _Package-by-feature_.

#### Package by layer

_Package by layer_ (or packaging by *horizontal slice*) is most common way
to structure project's classes. It supposes of focusing on the system logical tiers like controllers, domain, services etc.

~~~
|-- com.itexus
|   |-- controllers
|   |     |-- UsersController
|   |     |-- GamesController
|   |     |-- ...
|   |-- domain
|   |     |-- User
|   |     |-- Game
|   |     |-- ...
|   |-- views
|   |     |-- UserView
|   |     |-- GameView
|   |     |-- ...
|   |-- services
|   |     |-- UserService
|   |     |-- GameService
|   |     |-- ...
|   |-- dao
|   |     |-- UserDAO
|   |     |-- GameDAO
|   |     |-- ...
|   |-- ...
~~~
The advantages of this solution is possibility to get reusable framework/libraries and better
separating and better "replaceability" of each layer in the project (for example UI replacing or several UI usage).
But in the same time such package structure means that each package contains
items that usually aren't closely related to each other. As a result, editing a feature
involves editing files across different packages. In addition, deleting a feature
can almost never be performed in a single operation.

#### Package by feature 

_Package by feature_ (or packaging by *vertical slice*) uses packages to
reflect the feature set. It tries to place all items related to a single
feature (and only that feature) into a single directory/package.
This results in packages with high cohesion and high modularity, and with
minimal coupling between packages. Items that work closely together are placed next to each other: 

~~~
|-- com.itexus
|   |-- users
|   |   |-- User
|   |   |-- UserDAO
|   |   |-- UserService
|   |   |-- UsersController
|   |   |-- ...
|   |-- games
|   |   |-- Game
|   |   |-- GameDAO
|   |   |-- GameService
|   |   |-- GamesController
|   |   |-- ...
|   |-- ...
~~~
This approach (according to the various internet sources) provides better 
modularity, easier code navigation and high level of abstraction. 
On the other hand it assumes that the UI code for a feature has a nice one-to-one
relationship with the model code for that feature. And that goes against
common development experiences. There are also some complex issues,
such as _circular dependencies_ and _where common mechanisms should be placed_,
developer will have to deal with on the large project.

#### What should I choose?

Both _package-by-layer_ and _package-by-feature_ have own pros and cons.
And I will say: "Choose whatever you like and whatever you feel safe with".
Although you might be would like to choose "middle ground", something hybrid like this:

~~~
|-- com.itexus
|   |-- common
|   |-- utils
|   |-- ws
|   |   |-- UserWebService
|   |   |-- GameWebService
|   |-- users
|   |   |-- User
|   |   |-- UserService
|   |   |-- UserDao
|   |   |-- ...
|   |-- games
|   |   |-- Game
|   |   |-- GameService
|   |   |-- GameDao
|   |   |-- ...
~~~
