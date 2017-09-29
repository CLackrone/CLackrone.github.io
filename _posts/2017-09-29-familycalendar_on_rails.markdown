---
layout: post
title:  "FamilyCalendar on Rails"
date:   2017-09-29 16:11:11 +0000
---


Well that was fun! I decided to create a family calendar as my first Rails app. As a busy mom I liked the idea of keeping everyone's activities in one place. 

In FamilyCalendar a user signs up and controls calendar events for all family members. The user can view all family members attending an event, view all events associated with a family member, and view events by category. 

I challenged myself to use Devise for authentication in my app because I've struggled with it in every lab prior to this. My biggest challenge was adding Facebook sign-up via Omniauth. I learned that when assigning the app_id and secret directly from Terminal, you must assign it in the window from which you are running your rails server. This caused me an hour of frustration, but I learned so much when trying to solve the issue. 

Another major challenge for me was building a scope method. It turns out I need to work more on SQL statements. 

Although I'm sure there are still some bugs to fix, I'm happy with the overall finished product!
