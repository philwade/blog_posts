I missed posting last week, and this week I'm also feeling pretty overwhelmed.
I'm working on finding a place to live and starting a job in a new city. So
instead of trying to come up with something completely new to write about and
missing a second week, I'm going to just relate a tale of code deployment gone
wrong.

  
Roughly three years ago, I was working, and at the time, the company was in a
bit of flux. The development team was understaffed, so with a ow level of
experience, I inherited the job of deploying the website to production.

  
This meant taking machines in and out of service by logging into the load
balancer, rsyncing new code to every machine, and then logging directly into
the production servers to clear cache before making them live again. Clearing
the cache was done by going into the cache directory and typing "/bin/rm -rf
." - it was necessary to do this because rm had been aliased to "rm -i", which
prompted for every file removed, mainly for safety reasons.

  
This process was careful work, but at the same time, it was quite tedious. So
while various tasks were running, I did what any good programmer does during
downtime. I dorked around on the internet.

  
So one day, while doing a deployment, I was looking at reddit. When I looked
up, my boss was standing over my shoulder - not just any boss, but the big
boss. I'm not sure how many management layers existed between us at the time,
but it was several. Needless to say, I felt a bit put off that I had been
caught screwing around. He had a question. I answered quickly, spun in my
chair, and executed the next command in my routine. "/bin/rm -rf ." Then I got
up to get some coffee.

  
When I came back, the command was still running, which was unusual. I didn't
think much of it until I saw a string of permission denied errors appear. That
was _very_ unusual. It had never happened before. That's when I realized I had
never changed directories to where the cache was. I had just removed
everything in the home directory. Which was also the web root.

  
Oops.

  
And that's why you automate your deployments.

(I eventually did)

