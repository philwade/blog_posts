I've written about this before, but at the risk of contradicting myself in the
future, I'm going to say I don't think I'll ever get tired of coming up with
command line solutions to little problems. The beauty of unix is the way that
you can stitch together programs to make your life easier.

  
It might be one of those things that I like because it makes me feel clever,
but if that is case, so be it.

  
The problem I was trying to solve was simple. I needed the current version of
an svn repository so I could insert it into another file during a build
process. Since we're running the script inside an versioned directory, the
command "svn info" will give us this.

  
` [pwade@web48 philwadeorg]$ svn info Path: . URL:
http://example.com/phil/trunk/philwadeorg Repository Root:
http://example.com/phil Repository UUID: 6596c492-bec3-4f50-a8a2-b0ff2d2738bf
Revision: 445 Node Kind: directory Schedule: normal Last Changed Author: phil
Last Changed Rev: 384 Last Changed Date: 2010-12-14 09:37:56 -0600 (Tue, 14
Dec 2010) `

  
Neat! We've got our revision right there: "Revision: 445". Too bad it's
surrounded by a bunch of crap that we don't want. Grep lends a hand here.

  
` [pwade@web48 philwadeorg]$ svn info | grep Revision Revision: 445 `

  
Much closer now, but we want just the number, nothing else. The next tool
we're going to grab is awk. If you're not using sed and awk, you really should
be. Unix is all about moving around text, and sed and awk are all about
manipulating that text, which, as you might imagine, comes in handy. My dad
passed down the O'reilly [Sed & Awk book](http://www.barnesandnoble.com/w/sed-
and-awk-dale-
dougherty/1100323264?ean=9781565922259&itm=1&usri=sed%2b26amp3b%2bawk) when I
started working, and it's been very useful. It sits on my shelf, and when I
need to figure out something like this, I pull it down and make stuff happen.

  
Anyway. Awk. At the most basic level, awk just takes a line of input, and
splits it into separate pieces, delimited by spaces. These are referred to
like so: $1, $2, etc. For each line of input, awk will act upon those pieces
how you want. In my case, all I want it to do is grab the second part of the
line (the revision number) and print it out. Here we go.

  
` [pwade@web48 philwadeorg]$ svn info | grep Revision | awk '{print $2}' 445 `

  
And there you have it. Our revision number from that big mess in just two
simple steps. I was going to run this command from inside a python script, but
it was actually easier to pass in the output as a argument to the script.
Funny thing, that python command line library.

  
It should be noted you could probably solve this problem with just awk alone,
or that there may be a way to get it out of just the svn command. I couldn't
find an svn solution in my (admittedly short) search for one, and I think a
pure awk solution would take a lot longer to cobble together.

