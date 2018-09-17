---
layout: post
title: Sprint 2 Review
date: '2016-02-26 12:07:13'
tags:
- dissertation
categories: dissertation
---

Today marked the end of Sprint 2, and I will move onto Sprint 3 today. 

{% include image.html file="sprint-2-burndown.png" description="Sprint 2 burndown" %}


The burn down chart shows I was completing work in this sprint to a good consistency. I continued from 21st - 24th completing the task "training handwriting data" which is an ongoing task so it does not have story points attached to this task. 
 
### What I actually did

I managed to be able to get a basic Flask python application which will allow a user to upload their images woring. Once the user has uploaded their image to the website then it will redirect them to a page which shows the note on the page. This was approached using TDD and has a good set of error cases. Additionally, security has been at the forefront of my mind when developing the application so additional checks have been made before saving the image to the file store.

I approached the initial application structure as a "traditional" MVC approach. There's a directory for routing and the blue prints, a directory for Models (which will contain the database logic as well as the service objects) and finally a directory for the view files.

Another major progress this week was removing the noise from a note. Previously my text segmentation from the image would include a lot of the noise. I opted to recode this, using the adaptive threshold previously mentioned I additionally investigated connected components. This involved investigating different morphological operations using the OpenCV library. 

Throughout the middle of the sprint I was unable to get the Travis CI script to auto-deploy to a server, and as there was insufficient documentation around this the task was dropped due to lack of time on the project.

I spent the remaining 2 days of the sprint training tesseract on this new improved algorithm. I did 4 iterations of training, and it returned a good accuracy. There were less dots and underlines, from additional noise on the image. It is also beginning to recognise words now such as "always" and "lecturer". Overall, there needs to be more training data applied because almost always the letter i gets tagged as 5, S, etc. 

### Things that went well 
* Got a good image segmentation script which can deal with a variation of lighting. 
* Did more training 
* Got the initial application ready to build upon. 
* Got a good series of tests.
* Created a set of CRC cards for design purpose.


### Things which didn't go so well. 
* Some of the quirks of Flask slowed me down. 
 

### Things which I intend to do better next sprint 
* I need more tests, both for the new script and tests using selinum which will check the page's content.


### What to do this sprint
Well, although this sprint will be less productive I have estimated to attempt to complete 18 story points. But I have to do a poster assignment regarding the dissertation for next Friday so I should concentrate on that. 

Regardless, I am dedicated to continue when I can, and I will be looking to do some meta-data tagging of the images. This will involve choosing an appropriate database. I will then be looking at saving this data as well as looking into the Google API for the integration with the calendar.

Hopefully I'll have things to show for the pre-mid project demo.
