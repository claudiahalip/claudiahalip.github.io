---
layout: post
title:      "One page application, one week to accomplish"
date:       2020-08-31 04:15:14 +0000
permalink:  one_page_application_one_week_to_accomplish
---


One page application , one week to accomplish.... I though it will be impossible .
But a good plan, as always, will save a lot of time later.
My idea for this project came from this quote of  Michael Palin, an English actor, comedian, writer, and television presenter.
“I am not a great cook, I am not a great artist, but I love art, and I love food, so I am the perfect traveller.”
My one page application is called “Trip and Treat” and it can keep track of your trips and what you enjoyed eating there. Anyone can share their culinary experiences while traveling and  inspiring others.
While building the backend with Ruby and Rails was pretty familiar from the previous projects, the most challenging thing for me was working on the frontend, especially coding in Javascript, a programming language which was something completely new for me.
There were 3 things which helped me a lot on this project:
-pseudocode -before every step I took I wrote down exactly what I needed to accomplish.
DOM manipulation- when I was learning about it I was asking myself, what are the advantages of doing this?
debugger - he was my friend all the way. Being able to see how my data looks like every time I needed to was the biggest benefit.
By the end of my project I’d learnt one important thing that slipped to me on the rails project.
I was implementing the delete function when I discovered that I could delete an object which was a parent object if the parent did not have any children objects, but I couldn’t delete it if the parent had children. The error I had in my terminal was:

ActiveRecord::InvalidForeignKey (SQLite3::ConstraintException: FOREIGN KEY constraint failed)

The quick fix was to add in my parent model  dependent: :destroy
Then parent.destroy will do the magic, deleting it,  including all the associated objects.
It’s been 6 months of learning to code.

