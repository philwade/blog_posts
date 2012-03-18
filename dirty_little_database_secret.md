Recently I tweeted about one of my blog posts, and surprisingly saw a mini
spike in traffic - when traffic is almost zero, any traffic is a spike.
Regardless, when slapping together this blog, in many places I took the path
of least resistance. With regards to database, that path was sqlite. I knew
full well that it couldn't hold up against any real sort of traffic, but the
idea of creating a database and users and yada yada yaaa was just not
something that looked like a lot of fun at the time. So I've been running the
site on sqlite.

Now back to that traffic spike - it got me thinking about using sqlite. Maybe
not so much thinking as worrying. Nobody wants concurrency issues. Nobody
really wants to switch database engines either. Both are unpleasant, but only
one affords the opportunity to learn PostgreSQL. I could have gone with MySQL,
which I have installed and know, but I've been on a bit of a learning kick
(this site is the product of that).

  
I installed the macports Postgres on my mac to teach myself how to port the
data from sqlite. Installing it that way was super easy. The hard parts were
installing the python database library and actually using Django's manage.py
to dump and reinstate the data. I won't go into my particular difficulties
(unless somebody asks) but lets just say manage.py makes it much easier than
it would be otherwise, but it still could go a ways towards making it easier.
After all, I'm no DBA :) I think I may continue to use sqlite in dev, but I'm
glad I got through the switch.

Overall, I've got a little Postgres experience now and I don't have to lay
awake thinking about my database concurrency issues.

