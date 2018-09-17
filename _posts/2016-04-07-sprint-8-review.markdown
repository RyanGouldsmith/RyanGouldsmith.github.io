---
layout: post
title: Sprint 8 Review
date: '2016-04-07 11:38:43'
tags:
- dissertation
categories: dissertation
---

Sprint 8 has been completed and it has not really been like the other sprints. As I feel I am approaching the end of the project, I have been completing issues I have come across so not as many story points have been included. 

{% include image.html file="sprint-8-burndown.png" description="Burndown chart sprint 8" %}

I completed most of the work in the beginning of the sprint, then turned some of the tasks to stories as they were too large and did a mid-sprint quick plan on those items. 

### What I actually did
The main aim for this sprint was to include Tesseract into the web app. This really does tie up the application and make it a valid bit of software for an end user. 

#### Tesseract Integration
With the initial epic-story of just been "integrate Tesseract into the system" I thought that was far too big of a task to estimate to complete. As a result I split the epic-story down into two stories: "*As a user, I want to be able to have automated suggestion of meta data from the image, so that I can know what to tag.*" and "*As a developer I want to integrate tesseract into the application, so it can read information from a note*". This gave me the clear distinction of actually getting Tesseract to work within the application and the other story for displaying content to the user. 

One of the first things to do this sprint was to implement the pre-processing script which I made to binarise the image. This was implemented into the upload route so that it converts the image to a tiff file, before running the Tesseract from it. 

I discovered that the Tesseract command line does not give you the ability to get the confidence scores directly; the C++ API does give you that functionality, however.

This ruled out writing my own wrapper for the tool without using the C++ library. However, I found this awesome library which would output the confidence score for each word identified. I investigated the [tesserocr library](https://github.com/sirfz/tesserocr) and found that this was suitable. Other libraries were available but they offered basic functionality for Tesseract and not outputting the confidence scores I wanted. 

I integrated this library into the application, and immediately thought of an issue: I need to constrain the notes so that they're consistent every time. Therefore it was decided that the first 3 lines of the image were to be the module code: title, date and lecturer. This would be the meta-data parsed from the image. 

After collecting the confidence score, I created a threshold for the values and returned whether they should be green, orange or red. The colour of the text indicates how confident Tesseract is that it's the word it's detected. This now resulted in Tesseract being fully included in the system, with colour codings on word confidence. 

{% include image.html file="tesseract-confidence-output.png" description="Confidence Tesseract Output" %}
#### Logout functionality
One aspect of the system I found that I was missing was a logout functionality. I had the sign in with Google sorted, but no sign-out. This was amended when I added a logout route and checking if the user id is in the session. If this route is hit then it will remove the user id and all of google credentials and they would have to tart again. 

#### Fixing things
I had to fix an issue with the timezone from a calendar event. Originally, I thought the issue was the comparison of the event summary when comparing module codes - but investigation showed that it was a timezone issue. This has now been fixed. 

I added some user experience features such as a datepicker and a timepicker. The default jQuery datepicker was used and a [this timepicker](http://jonthornton.github.io/jquery-timepicker/) was used. It required a large modification of all the tests and routing. 

A series of validation was added on both the client and server side when interacting with the form. HTML5 required fields were used and having previously used the pattern attribute, I went and tried to create a REGEX to avoid empty spaces in the input box. On the server side error catching was implemented and then sent to the user on the page to show any errors; the system feels a lot more robust now I have added these checks. 

Fixed an issue of every time a user logged in it would create a new user row - which is wrong. I added find or create functionality so now the user logging in with the same google email address will see their same notes.

Along with the log out route I fixed the invalid grant that than happen when the token expires in the session and that is used to try and connect to Google. This has happened a couple of times so this has now been fixed. 

Finally, I have redesigned the website gave it all consistent stylings and made the information more accessible and easier to see. Additionally, it should be responsive now too. 

{% include image.html file="tesseract-confidence-ui.png" description="Redesign of Tesseract confidence " %}
{% include image.html file="events-calendar.png" description="Redesign of App" %}

### Things which went well
* Got a lot of the little bits which make the system better as a whole done. 
* Stuck to TDD well this sprint. 
* Happy to have almost finished MVP. 

### Things which didn't go so well
* Refactoring: Although TDD has been practiced I think on a couple of occasions I could have refactored it better.
* Travis CI build time is now high

### Things which I intend to do better next sprint
* More merciless refactoring. 

### What to do this sprint
From some pre-beta comments from both my supervisor and a couple of peers, I will be implementing a click on the tesseract information and it will populate the text boxes for you automatically. 

I will also be looking at when you edit the meta-data it will update the calendar item and put the new item in the updated date's calendar item. 

Then more of the report :) 