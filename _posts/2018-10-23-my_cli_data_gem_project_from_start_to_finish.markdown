---
layout: post
title:      "My CLI Data Gem Project, from start to finish"
date:       2018-10-23 20:33:31 +0000
permalink:  my_cli_data_gem_project_from_start_to_finish
---


# My CLI Data Gem Project, from start to finish

Deciding on the topic was probably the quickest and easiest part of this project.  I love running in the pristine trails of the Pacific Northwest, so I decided to scrape the webpages of two of the largest organizers of trail runs in my home state of Washington.

From there, I followed along with the videos pretty closely and built out a basic application.  It featured a CLI interface class and a Run class.  The CLI class handled all of the user interaction, whereas the Run class did all of the scraping and and organized the data into hashes.  This part was fairly straightforward and didn't take too long, although a few typos and other errors slowed me down a bit.

The most complicated and difficult part of the process was scraping the data.  Each website presented its own challenges here. 

Evergreen Trail Runs--
Only has one event featured on their site at the moment, so I thought it would be fairly simple.  However, I needed to scrape from both the surface as well as the 'events' page, and I discovered that the HTML of the site was not conveniently organized.  Some of the elements I was scraping were deeply nested in structures without ID or Class identifiers.  This resulted in long and complicated selectors.

Northwest Trail Runs--
Also seemed fairly simple at first.  All of the data I needed was there on the 'Events' page, and it was fairly straightforward to get the first event.  Later on, when I tried to add more events from this page, I discovered that there were inconsistencies in the formatting of the elements.  This caused a lot of head scratching at first, but I was eventually able to locate a selector that would work for all of them--almost.  I realized that the last element in their 'Events' page didn't feature a registration link, and was causing my loop to break.  I tried a number of ways to fix this, but ultimately decided not to scrape *all*  the events, but rather just the next few.  This way, my CLI would feature a neat and tidy 5 items, rather than 11.   

Once I had working data and a clean interface, I went about refactoring.  The scraping methods were all switched to a Scraper class, with the Run class acting as an intermediary.

One weakness of this app is that it does favor events from Northwest Trail Runs, because Evergreen has only one event featured at the moment.  When Evergreen gets around to posting more events (likely next year), the program will still only feature the first event on their page.








