I like to keep my stuff backed up. I've got a huge external drive next to my
laptop that I use as a mac time machine. For stuff like tax backups, I also
throw a copy in my dropbox. And another on my web server. I used to put a copy
on a thumb drive. I wish I could find the source of a piece of advice I once
read, but my google skill is lacking today. Basically, the jist was: "If you
have _n_ copies of something, you really only have _n - 1_ copies for all
practical purposes." If you only have one copy of anything, you could find
yourself without that thing any moment.

  
Making bunches of copies may also appeal to my inner hoarder sensibilities
without taking up extra space in my house, but I'm going with the "just being
safe" argument. At least publicly.

  
Either way, I realized just the other day that, to my horror, the only copy I
have of my blog is the single database at my web host. I know for a fact that
they do regular backups, but for my own piece of mind, I'd like to have copies
myself.

  
So I wrote a little script that hooks into my django models, converts my posts
to markdown formatting, and saves them to flat files. It also saves some meta
data about each post in a related json file. At the moment it's nothing to
write home about really, and it messes up the markup that I use for code
blocks, but it's a good enough backup for most purposes. I plan on extending
it a bit so that I can write posts as flat files and have them converted to
html and synced back out to the live site, automatically push the copies to
github, etc.

  
That's the other advantage. Now that my blog posts exist outside of a
database, I can push the markdown files out to github. That way, if my grammar
sucks or something, anyone can correct it and submit a pull request. That's
assuming anyone cares to correct my grammar, but let's not get all academic
here.

  
You can check out my backup script
[here](https://github.com/philwade/blog_backupper), and the repository with
copies of all my blog posts [here](https://github.com/philwade/blog_posts).

