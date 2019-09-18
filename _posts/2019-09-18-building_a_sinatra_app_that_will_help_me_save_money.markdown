---
layout: post
title:      "Building a Sinatra App that will help me Save Money "
date:       2019-09-18 12:11:05 +0000
permalink:  building_a_sinatra_app_that_will_help_me_save_money
---


As a mum with a busy household to run, it is important to me that I stay on top of things lest there will be chaos and then my brain will just go into meltdown. I love being organised and making lists and so for this project, I decided to build something that can help me keep track of all the voucher or discount codes that I find or get from various places - leaflets, newspapers, shop promos, you get the gist! 

Although very basic, it does a good job of storing the shop name for which the voucher can be used as well as other key information such as the actual discount code, expiry date and how much savings you can get. I would definitely spend more time refining it and making it look pretty but for now, I'm still proud of what I have built. 

It helped solidify my understanding of the MVC structure, CRUD (Create, Read, Update and Delete), ActiveRecord Associations and RESTful Routes. 

The **Model-View-Controller** framework is a popular way of structuring the program's files and maintaining *separation of concerns*. I think understanding this concept considerably helped to make the building process feel a lot more manageable.  

* **Model** - contains the underlying logical structure of the application and where the high-level classes are defined. 
* **View** - contains the information about how your pages should be rendered i.e. user-interface
* **Controller** - contains the information about the processes that connect the model and the view (including handling input)



Sinatra allows us to bring these together with **CRUD actions** to build this simple Voucher Tracker app. 

* **Create** - in Sinatra by building a route to render a form for creating a new instance of a model. In my app, an example would be the Sign Up form to create new instances of users and the Submit a new code form that creates new instances of vouchers. 
* **Read** - I enabled my users to *read* all the instances of a class via the "vouchers/index" erb page or only a specific instance of it via the "show" erb page. 
* **Update** - the users can edit the details of the voucher code. I enabled this by rendering an update form and a controller action to catch the post request sent by that form. 
* **Delete** - is a delete button that is included in the "show" erb page. 

**Other things I learned: **

Apart from implementing the above actions, I had a lot of practice in implementing associations between classes or models via ActiveRecord. 

For my app, a User model can have many Vouchers and so this was implemented simply by adding `has_many :vouchers`  within the User model and `belongs_to :user` within the Voucher model. 

```
class User < ActiveRecord::Base 
  has_secure_password
  validates :email, presence: true, uniqueness: true 
  validates_presence_of :password
  has_many :vouchers 
end
```

```
class Voucher < ActiveRecord::Base 
  belongs_to :user 
  belongs_to :store
end 
```



At the same time, to enable the association to be reflected on database, I needed to create a column for the user_id in the vouchers table. I implemented this by adding a `belongs_to` reference as below: 

```
class CreateVoucher < ActiveRecord::Migration
  def change
    create_table :vouchers do |t|
      t.string :store_name
      t.string :code 
      t.integer :savings 
      t.date :exp_date 
      t.belongs_to :user 
    end 
  end
end
```

These neat and simple lines are called macros which adds a number of methods to the class which are specialized according to the collection or association symbol and the options hash. 

Lastly, for this project, we were required to implement a user login and authentication with the help of the `bcrypt` gem which is a hashing algorithm that helps store user passwords securely. In my project, this translated to adding a few lines of code including `has_secure_password` in the User model as well as using other methods such as `user.authenticate()` as per below: 

```
def login(email,password)
    user = User.find_by(:email => email)
      if user && user.authenticate(password)
        session[:user_id] = user.id 
      else 
        redirect '/login'
      end 
    end
```


All in all, I really enjoyed putting this app together although there were moments when I thought I was ready to admit defeat. In these moments, it really helps to take a step back and approach the problem with fresh eyes. It also helps to have your notes and material at hand so that you can review the concepts when you are stuck. 



