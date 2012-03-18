Version control is the software miracle that nobody seems to know about until
they get their first job. I've read plenty of forum posts from computer
science students asking "What don't they teach you in school?", and inevitably
the first response is about version control. It was true for me.

  
Even for solo development VC is great, and since I've known about it, I've
hosted all of my code in a private Subversion repository. This makes working
on my code from anywhere easy, and has the added benefit of keeping a backup
of my work.

  
Just as I was becoming comfortable with Subversion, newer distributed version
control systems popped up. As the hype around both Git and Mercurial grew, I
decided it would be in my best interest to bring myself up to speed. At work
we considered switching to Mercurial, mainly on the grounds that it had wider
operating system compatibility, so I created myself a Bitbucket account to aid
in learning. At the time, Github was exclusively git, and Bitbucket
exclusively mercurial.

  
Both Bitbucket and Github brand themselves as "social coding" websites, but
even as I began to use my Bitbucket for all my non-private projects, I never
really thought about it. My main reasoning for using it was as an added facet
to my resume. Because of the nature of programming, it is sometimes difficult
to express your ability level, especially in an interview. Being able to point
someone at a big pile of code you've written is helpful.

  
I really discovered why the "social" aspect of these sites is a big selling
point a couple of weeks ago. I posted about
[GreyHolder](https://bitbucket.org/pivotal/greyholder), a little jQuery plugin
that I wrote and released on my Bitbucket. What I didn't realize was that is
contained a bug that could potentially throw away user input. Not very cute
behavior for something that is supposed to make life easier on the user. I
didn't notice the bug, but my friend [Dan](http://operatorerror.org/) did.
Because the code was on Bitbucket, he was able to grab it, fix the bug and
then send me a pull request to grab the fix. That meant that all I had to do
to fix the problem was click a button accepting his new code.

  
I don't know if you've ever fixed a bug with the press of a button, but it's
great, and it should be (and is) the main selling point for code hosting
sites. That capability is the reason I'm going to be using code hosting for
all my future projects, even the private ones.

