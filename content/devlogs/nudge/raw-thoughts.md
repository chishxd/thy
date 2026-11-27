+++
Title = "Just some raw thoughts"
draft = true
date = "2026-11-27"
+++

I was thinking alot on this and realized it's already 7PM. Instead of locking in a final format, with consideration for everything. 
I will start with most basic stuff.

A task defaults to reminding every 4 hours (6 reminders a day looks fine to me -- most of the time the laptop might not even be open
so it's max 4 reminders ig) and if proper time and date are specified then it's one shot, if only time then daily recurring at 
said time and if only date, then reminder every 4 hours only on that day. As for weekdays and modifying every N hours reminders.. 
I will think about them later. And yeah I was already thinking of hook script.. 
It can be anything you want, I would only be responsible to trigger that script.. Well then what is cron job for? It does the same
thing!! Wait no it doesn't it does not have priority stuff, It won't mark something automatically as "done" either..

So a line in this file of mine.. I think it will look like this for now:

```
priority | time | date | message
0 | 21:00 | Read ASOIAF
3 | 06:00 | 2026-11-20 | Submit Maths assignment
```

wait.. In the date part.. I could also just make it relative time.. like 2d (in 2 days) or Mon (next Monday).. if I do that I can 
automatically have Mon-Fri, and it will only trigger recurring from monday to friday. I am so smart.. and if someone omits Time 
and only writes Mon-Fri, then they will get reminder every 4 hours for entire week!! I can do similar thing in Time I
guess, like if someone does 5h it will remind in every 5h.. unless they specified date to be only today.. 
if they want one shot reminder, make the date and time specific too! Daym I am so smort. But relative days like
2d will only work with CLI, as file would always only be 2d and nothing else.. We can make it a future scope to make a better
daemon feature to make tasks to be like objects and compare their creation timestamp with current time stamp..
Kinda intermediate scope... but will make the project a 20 h project lol.

And I can just omit the top priority, time, date and message part, It is just to let you know what I meant :p
So important part would be to have 0-- the priority, if no priority then default to 0-- like file MUST contain that 0
or they see error, but CLI can omit priority and it appends 0 to file anyways, and then the message. Everything else is
optional with same defaults.

The columns can just like be... we know priority is first and message is last.. And those are the 2 that happen to be only REQUIRED
ones. And anything that comes in between them happens to be time and date.. Maybe we could make it easier to parse by updating line
structure... 

new idea for line structure

<priority> "Message" @<time> @<date> 

Priority and message, required ones are at start.. And time date come later, identified by @ before them. 
