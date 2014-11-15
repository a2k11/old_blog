---
layout: post
title: It's Always Sunny in ... the Request, Response Cycle
---

### A Rails Application and the Web Server

With an internet browser, the user can interact with your application.  My job is to build
this application.  It is  difficult to become a master of developing rails
applications if I don't understand what is happening behind the scenes.  The web
server is a central part of the operation.  The request, response cycle
describes the sequence of events through which the server handles and processes
information.

*Frank, Dee, Mac, Dennis, and Charlie could create a rails application but it
would be horrible.  Everything would go wrong and nothing would work.  It is one
of my favorite shows because it's full of hilarious irony.  So we can refer
to the user as Charlie since the others would vote him out due to creative
differences.*  Charlie interacts with the browser which shows your web
application.  Then Charlie clicks a button and that makes a request to the
server.  This request hits the web server where it first sees Rack.  Rack wraps
HTTP requests into a single method call to interface with Ruby web applications.
It's a very useful API especially if you're creating a Rails application.

*At this point you would probably think Dennis would announce himself as the
manager.  It normally would be but Dennis is too obsessed with writing the about
page to be just about himself.*  The request now sees the Rails application.
The routes ( *location in the application: config/routes.rb* ) are used to figure
out where the application needs to go.  It matches the request with the
specified controller and controller action to perform.

The controller can be seen as the director of the rails application.  It
organizes the actions and contains their definitions made by the developer.  *Frank
would in charge of the controller and would make Dee in charge of the Model.  
Frank is funding the operation so whatever he wants will happen.  He corrupts
Dee into taking care of the information due to his manipulative ways.*  The
controller calls out to the model if it needs to access the business logic.
Databases are what models use to organize the information for an application.
Postgresql is a database which uses SQL to access, update, delete, and create
data objects.  The controller can also renders views at the end of the interaction
with the model.

*Mac wants to be the face of the application.  He wants the fame and success of 
this whole process.  Mac ends up being the view after all the actions have been
processed.  He will secure the app and restore the order, like he always does.*  
The views are what the user sees.  The controller specifies a view after it 
gathers all the information and conducts the actions which we define.  The view 
could contain JavaScript, CSS, and ruby code.  Our HTML documents are named
according to which programmable language we embed in the files (mac.html.erb, 
charlie.html.css, frank.html.js, etc.).  The response is now sent back to the 
web server and then to the browser where the user can view the newly rendered page.

After all this, the gang just decided to scrap the whole idea and figure out a
way to get their money back.  *It's Always Sunny in the Request Response Cycle.*
