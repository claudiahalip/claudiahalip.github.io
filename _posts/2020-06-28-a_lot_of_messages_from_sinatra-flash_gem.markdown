---
layout: post
title:      "A lot of messages from "sinatra-flash gem""
date:       2020-06-29 03:31:48 +0000
permalink:  a_lot_of_messages_from_sinatra-flash_gem
---



     Working on my Sinatra project I was thinking that it will be nice to be able to return all kinds of messages to the users when they do something on the application that they’re not supposed to do.
		 
       So I came across Sinatra-flash gem watching my one of my coach lectures. I was very impressed with this gem and I wanted to use it into my application. It took me some times to understand how it worked and how to make it work into my application. Here are my steps:

1. Install the gem by typing gem install sinatra-flash in your terminal(or add it into your gem file and then bundle install).

2.Require the gem on envirament.rb  file: require 'sinatra/flash'

3.In your ApplicationControler , inside your configer block you need to enable sessions by adding  enable :sessions  (Sessions allow your browser a way to persist certain information.You might enable session for persisting your user presence.)

4.You need a way to show  the messages so I chose to add them on layout.erb file, right before yield block so they can be available on any page I use them. So I added this:

<% flash.keys.each do |k| %>
    <%= flash[k] %>
<% end %>

The above block of code goes through each flash key, and for each one, prints the text associated with that key.
You need to set a new key-value pairing in any of your controller file. For example, I used the following code:

 delete '/items/:id' do 
      item = Item.find(params[:id])
      if logged_in? && item.user == current_user
          item.destroy
        else
          flash[:message] = "Not yours to edit this item"
        end
        redirect "/users/#{current_user.id}"
     end 


So when a user tries to edit  one item  posted by another user they will see a message that explains why they cannot edit  it.

It’s been 4 months and 1 week of learning to code!
