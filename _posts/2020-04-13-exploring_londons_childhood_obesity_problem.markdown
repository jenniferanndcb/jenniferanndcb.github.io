---
layout: post
title:      "Exploring London's Childhood Obesity Problem"
date:       2020-04-13 13:42:42 +0000
permalink:  exploring_londons_childhood_obesity_problem
---


For my final portfolio project, I decided to try and build an app related to public health. London has particularly high proportion of school-aged children aged 4-5 and 10-11 who are overweight and obese. I wanted to focus on shining a light on this issue by sharing the data available from Public Health England's [fingertips profile](https://fingertips.phe.org.uk/). I visualised the finished product to be a chart that will enable users to browse and display and compare data across different areas in London. 

I started by downloading the childhood obesity profile in London in a CSV format.  This includes a breakdown of prevalence rates in 32 different London Boroughs* for the sets of age groups (4-5 year olds and 10-11 year olds). 

I then loaded and used the datasets to build my Rails API. At this stage, I learned about DB Browser for sqlite along with the various Rake Tasks which I used to create my database. 

Once my API was up and running, I went straight into building the frontend with React/Redux. 

The Redux store holds the entire state of the application. I decided to use Redux as I knew that I would need a number of components to access and use this state. 

Thinking in terms of *actions* and *reducers* in Redux also helped me understand separation of concerns or responsibilities and subsequently organise my code. 

A crude representation of the structure goes like this: 

![](https://photos.google.com/search/_tra_/photo/AF1QipNB3G8VLH7wQsX2KrZtuq5UAN1Y_2rAK04sshl0)

Sticking to the topic of convention and organising code, it also helped to keep reminding myself that while building my React components, **only the containers should know Redux**. Components can access the data by passing the data that we need down as props as per below:

![](https://photos.google.com/search/_tra_/photo/AF1QipP4C9rNDdKBjt736mmMO0Vsgfb1VgE6-_09fnLD)

**Conclusion**

I thoroughly enjoyed learning and building this React/Redux application although I have had a lot of challenges along the way (including the fact that we are in the middle of a pandemic). There is a lot to learn but frontend development as a career, specifically in React is looking like an attractive and enjoyable path to go into. 



*The data for City of London (33rd London Borough) is combined with Hackney data due to small numbers. 






