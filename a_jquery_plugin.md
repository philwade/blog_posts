The other day, in line with my [goals for the
year](http://philwade.org/post/new_year_projects/), I was working on my family
gift distribution project [ White Elephant](https://bitbucket.org/pivotal
/white-elephant). One of my goals for the project has been to push myself
toward better page and user interaction design. I've always been a back end
sort of guy, telling myself that because I had the know how to code things
that I had no reason to care about how those things looked or felt to a user.
I've come to realize that assumption is pretty stupid. Taking time to not only
make things look pretty, but also make them easy to use is what sets apart
outstanding projects from the crummy ones. At this point, I'm a ways from
creating the cool things that I want, so actively making myself practice is a
step in the right direction.

  
So back to the main point. I was putting a very stripped down form into a
confined space, and instead of having a label next to each input, I thought it
would be neat to have some greyed out text that told the user what went in the
box. When they clicked the input, the text would disappear and the text they
typed would look normal, not greyed out. If you clicked away without typing
anything, the original hint text would come back. It looks like this:

  
  
  
I thought it was a clever solution, and that perhaps others would like to use
it, so I wrote it as a jQuery plugin. This was a process that took me through
the weird world of javascript objects and closures. Things I've touched
before, but they always seem a little weird. I found the [tutorial on writing
jQuery plugins](http://docs.jquery.com/Plugins/Authoring) very helpful, and
quite instructive about javascript objects as well. You can get the plugin
from my [bitbucket](https://bitbucket.org/pivotal/greyholder).

  

