---
layout: post
title: First Post
---

### It's Always Sunny in ... the Request, Response Cycle

With an internet browser, the user can interact with your application.  My job is to build
this application.  It is  difficult to become a master of developing rails
applications if I don't understand what is happening behind the scenes.  The web
server is a central part of the operation.  The request, response cycle
describes the sequence of events through which the server handles and processes
to and from a user's browser.

*Frank, Dee, Mac, Dennis, and Charlie could create a rails application but it
would be horrible.  Everything would go wrong and nothing would work.  It is one
of my favorite shows and I laugh every time I watch an episode.  So we can refer
to the user as Charlie since the others would vote him out due to creative
differences.*  Charlie interacts with the browser which shows your web
application.  Then Charlie clicks a button and that makes a request to the
server.  This request hits the web server where it first sees Rack.  Rack wraps
HTTP requests into a single method call to interface with Ruby web applications.
It's a very useful API especially if your creating a Rails application.  

*At this point you would probably think Dennis would announce himself as the
manager.  It normally would be but Dennis is too obsessed with writing the about
page to be just about himself.*  The request now sees the Rails application.
The routes, *location in the application: config/routes.rb*, are used to figure
out where the application needs to go.  It matches the request with the
specified controller and controller action to perform.  

The controller can be seen as the director of the rails application.  It
organizes the actions and defines them based on coding by the developer.  *Frank
would in charge of the controller and would make Dee in charge of the Model.*  The
controller calls out to the model if it needs to access the business logic.
Databases are what models use to organize the information for an application.
Postgresql is a database which uses SQL to access, update, delete, and create
data objects.  The controller also renders views at the end of the interaction
between the controller and model.

*Mac would want a huge part in the fame and success of this whole process.  In
this scenario he would be the view after all the actions have been processed.*
The views are what the user sees and the controller specifies a view after it
gathers all the information and conducts the actions which we define.    The
view could have some JavaScript, CSS, and ruby code inside each HTML document
which is why we name our files accordingly (mac.html.erb, charlie.html.css,
frank.html.js, etc.).  The response is now sent back to the web server and then
to the browser where the user can view the newly rendered page.
