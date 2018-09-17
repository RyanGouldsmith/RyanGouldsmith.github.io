---
layout: post
title: Sprint 9 Review
date: '2016-04-14 11:29:35'
tags:
- dissertation
categories: dissertation
---

Today I start Sprint 10 - finishing Sprint 9. This sprint has felt like a mixed bag really. 

{% include image.html file="sprint-9-burndown.png" description="Sprint 9 review" %}

As I am in the tidying up process I only estimated 18 story points which I completed rather quickly. 

### What I actually did 
The main aim of the sprint was to complete the edit functionality with the calendar. It would work in such a way, that if you edited the calendar it would remove old description events and add it to a new event if found in the calendar. 


#### Edit Calendar items
The story "*As a user I want to be able to edit the date and update my calendar*" was created due to a meeting with my supervisor who suggested that when the user edits and updates their note meta-data then it would reflect that in the calendar entry. In simpler terms: I needed to be able to remove event description from one event and plonk it in a new event, if it exists. 

The Google Calendar is slowly becoming the bane of my life. Initially I was just replacing it with an empty string. However, I discovered that this would be terrible if some useful information was placed in the description field. This was refactored and changed to do a find and replace as well as an append to the end of the event description. 

#### Tesseract helpers
A user interface and user experience feature was developed under the story: "*As a user I want to be able to click Tesseract Items, so that it's easier for me to put in the fields.*". This was suggested after some pre-beta over the shoulder looking from my supervisor and my peers. 

Now the divs are clickable and it will populate the text-fields on click. This was quite simple to do with a bit of jQuery. Additionally, I added some functionality to check to make sure that the tesseract variables are valid before letting you click on them.

#### Refactoring
I did a lot of refactoring on the system. With the functionality for the edit calendar being introduced it meant that in a lot of places I was writing lines and lines of code which did the same functionality - this is not good for the DRY(do not repeat yourself) ideology. As a result I spent over 2 days refactoring the code back to be as clean and readable as possible. I introduced a series of helper classes and service classes where appropriate. 

The system is a lot more readable now and I have tried to reduce the amount of similar function calls as possible. 

#### Other things 
I worked on the report, getting a good headway into the background chapter; analysis was conducted on OneNote, Google Keep and EverNote for comparisons of similar related systems. 

On Thursday, during the group meeting, I tried to do a "user study" but, naturally with any demonstration, the application decided to break. Interestingly, I found some use-cases I had not considered, so not all was lost; when parsing an event from Google I had not considered all day events - and these do not have a dateTime field. 

Additionally there was an issue with the tesseract and parsing the lines of text throwing an index out of bounds exception. This has now been caught and tested.

One thing I have noticed this morning was reoccurring events being a pain. When you make a request to the service it only gives you the time it was first created. So when I got an event saying 20th February, when it was supposed to get an event from the 12th April then I was naturally super confused. This will be fixed ASAP. 

Additionally, I have CSRF support added to the application and ready to merge in. 

### Things which went well
* There's now a nicely engineered system. 
* TDD to test the application. 

### Things which didn't go so well
* The demonstration, due to issues I had not considered.

### Things which I intend to do better next sprint
* Be able to demonstrate the application.

### What to do this sprint
* I need to fix this reoccurring event issue ASAP. So I will be working on that.
* I need to pick up the pace on the report and get at least the design section written by the end of the next sprint. 

The sprints have slowed down a bit and I need to think in a way to do the user story points for the coming tasks, especially with the report. I am not entirely sure how they're going to work, but I will see. 

