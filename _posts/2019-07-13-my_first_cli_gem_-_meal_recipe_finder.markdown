---
layout: post
title:      "My first CLI Gem - Meal/Recipe Finder"
date:       2019-07-14 00:38:19 +0000
permalink:  my_first_cli_gem_-_meal_recipe_finder
---


Having a small family, I decided to focus on creating a CLI gem that I would personally use. Looking at practical challenges, I thought I should address my daily challenge of cooking healthy meals for my growing family. This led to the creation of my first CLI Gem which works as a Meal or Recipe finder using the [BBC Good Food website](http://https://www.bbcgoodfood.com/recipes). 

I was very excited by the prospect of bringing this idea of mine to life but at the same time I was quite overwhelmed by the skills required to complete the project. I had to remind myself that I have completed the first section of the curriculum and so I should be well-equipped to build a success out of this project. Anyways, it took me a while to get over my self-doubt and for me to 'just get on with it'. 

In this blog, I decided to talk about the approach that I took in building the gem as well as the lessons that I have learned. 

**Planning**

In planning the gem, I made sure that my idea was crystal clear in terms of what I wanted it to do before I started to write a single code. I even got carried away in my notes and included lots of features which I decided to scrap as I realised there is no need to make my life more complicated... perhaps when I'm a fully-pledged software developer and have more time. 

Anyways, I settled on providing the user an opportunity to browse BBC Good Food's recipes by course. 

Upon choosing their desired course of meal, the user will be presented with a list of recipe suggestions. 

The user can choose a recipe and find out how to make it 

Keeping it simple! 

**Start Coding**

Once I had a clear idea (not necessarily detailed), I started to dive into writing my code. A lot of my initial code, I've now deleted but what I've learned is, coding is like a journey. Your code won't be where it is now if it wasn't for the previous code that you wrote. I don't know if that makes sense but I guess what I'm trying to say is every code that I wrote led me to thinking about my solutions. 

I also decided to work on this project locally (i.e. in my machine) so I took some time installing and setting up my editor, etc. I decided to use Visual Studio Code as it is free and seems straight forward to use. 

**Challenges**

Getting the code to work. I wanted to say that I followed the red, green, refactor principle but without the spec, it wasn't that colourful. I encountered a lot of syntax errors in the beginning which may have caused a couple of sleepless nights but with hindsight, I just needed to get used to coding without the helpful rspec tests on learn.co and pay attention to the details. 

I also had fun (and a lot of headache) with scraping. I learned that you really have to be careful in choosing the CSS selector particularly if you are using an enumerator - make sure it is a level above the nodes that you would like to iterate. 
Again, attention to details is key. 

**Lessons**

Get the CLI to work but don't be afraid to break the programme! I realised that this is sometimes necessary to move on. 

As an example, when I first started to write code, I didn't really think about the folders and files. Only after I finished my logic and got the whole thing to work, I decided that I need to move things around. Mainly to follow the Single Responsibility Principle (SRP) which led to my gem having these four files: 

* **cli.rb** - as the CLI controller, this file handles the displays and logic 
* **course.rb** - initializes and saves course object from scraped data
* **recipes.rb** - initializes and saves recipe object from scraped data
* **scraper.rb**  - scraping 3 levels of data from courses to recipes and recipe details 

Refactoring also made my program break a couple of times but nothing major as by the end of it, I felt more confident about where I might have gone wrong. 

So now my CLI works, I am just waiting for the assessment day for further feedback and ways to improve it but needless to say, this first project really challenged me and was a good way to consolidate everything that we learned in the last 2 months. 









