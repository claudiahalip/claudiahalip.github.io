---
layout: post
title:      "The elegant collection_select method"
date:       2020-07-31 10:34:24 -0400
permalink:  the_elegant_collection_select_method
---

Working on my Rails Project I can say that the most elegant  helper  method is 
collection_select. What a simple way to display attributes for a viewer to choose from.
The most effective way to explain this method would be by example.

So I have :

class Business < ApplicationRecord
   belongs_to :category
end

class Category < ApplicationRecord
    has_many :businesses
end

 Also, my business table has the following columns:
   
     "name"
     "description"
     "website"
     "phone_number"
     "category_id"

On my application  I want to have a form where my user can create and display a business. Everything is very simple until "category_id". I cannot let my user to fill in  "category_id" .How can she/he know what id each category has. I wanted to display a collection with all the category names to choose from. So here comes “collection_selector” in handy. The documentation says:

collection_select(object, method, collection, value_method, text_method, options = {}, html_options = {})

So, let’t take the argument one by one:
  -object: is the object I am creating the form for, in my case business
  -method:  is one of my object(business) method , category_id which will 
set the id attribute of the <select> tag
  -collection: is the array of all the category objects I have in may database, Category.all of course.
 -value_method: will be the value attribute of each option tag  :id(the id of the category-user’s selection)
-text_method: is what the viewer sees and can choose from :name(the name of the category)
-options = {} it’s a simple hash. The docs for what can be passed inside of is interesting and can be viewed here: https://api.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html
 For my form I chose this:

:include_blank => 'choose a category'

 At the end my collection_select will look like this :
collection_select @business,:category_id, Category.all, :id,  :name, :include_blank => 'choose a category'
I have just a few categories in my database but look how many lines of html this elegant method wrote for me, imagine when I will have hundreds:

  <select name="business[category_id]" id="business_category_id"><option value="">choose a category</option>
<option value="1">photography</option>
<option value="2">videography</option>
<option value="3">publisher</option>
<option value="4">air conditioning &amp; heating service</option></select>





It’s been 5 month of learning to code.

