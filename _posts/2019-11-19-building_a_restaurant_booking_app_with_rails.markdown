---
layout: post
title:      "Building a Restaurant Booking App with Rails "
date:       2019-11-19 16:14:59 -0500
permalink:  building_a_restaurant_booking_app_with_rails
---


For my Rails project, I decided to move away from trying to solve practical everyday problems (see previous projects re MealFinder and VoucherWallet) and instead build an application that will enable me to really consolidate all the topics and my learning from the Rails section of the course.  

DineOut is a very simple restaurant finder and booking application that allows users to browse restaurants and book a table at the time that is convenient to them. The app is not complete in that it doesn't take into account a restaurant's opening times and other operational factors. It is very basic but it has the functionalities that I need to demonstrate my understanding of the Rails. 

**Planning**

From the start, I knew that I would need three models one of which would be a join table (represented by a has_many :through association). I started thinking about what attributes that I need to get my webapp to work. This was the first mistake, in hindsight, I really should have started with the most basic attributes that I need. To demonstrate, here's what I started with: 

```
class CreateRestaurants < ActiveRecord::Migration[6.0]
  def change
    create_table :restaurants do |t|
      t.string :name
      t.string :location
			t.string :description
      t.string :website
      t.string :phone_number
      t.string :opening_hrs
      t.integer :ratings
      t.integer :capacity

      t.timestamps
    end
  end
end
```

And here's what I have in my schema now: 

create_table "restaurants", force: :cascade do |t|
    t.string "name"
    t.string "city"
    t.string "website"
    t.string "phone_number"
    t.integer "capacity"
    t.datetime "created_at", precision: 6, null: false
    t.datetime "updated_at", precision: 6, null: false
    t.integer "user_id"
  end

I removed the description and opening hours as they were distracting me from getting the app to work.

Once my models and associations are in place, I started drawing out the views that I wanted to see and the controller actions and routes that came with it. 

**Challenges**

Working on this project really helped solidify my understanding of ActiveRecord Associations and Rails Routing.  

ActiveRecord Associations

In particular, using scopes to narrow a database query and building this query so that it can be referenced as method calls on objects.  

Rails Routing 

I had not quite realised how flexible the Rails Routes are. I spent several nights trying to work out how to build a route that includes a dynamic class attribute. More specifically, I wanted users to be able to browse restaurants by city which is an attribute of a restaurant. I wanted to avoid unnecessarily creating a separate model for city (which I seriously considered towards the end to make my life easier). Anyways, in the end I settled with this implementation

```
resources :restaurants, only: [:new, :create, :show, :edit, :update, :destroy] do 
    resources :bookings
 end 

get '/:city', to: "restaurants#index", as: "restaurants_by_city"
```

**Lessons**

Next time, better planning and understanding of what I am trying to achieve would help speed up the process. I have struggled with time as I spent disproportionate amount of time on different parts of the project. 
