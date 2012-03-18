Hillary is out seeing a play, so I've had a whole afternoon to watch the Mets'
game and play around on the computer.

  
First up, although I didn't actually work on it today, I've now got Othello
code for everyone to download - take and look and give it a whirl:
[Othello.py](http://img.philwade.org/code/Othello.py)

I would love feedback (especially on my python skill/unskill). Here's a quick
usage example: ` phils-macbook-2:othello phil$ python Othello.py 7 | | | | | |
| | 6 | | | | | | | | 5 | | | | | | | | 4 | | | |w|b| | | 3 | | | |b|w| | | 2
| | | | | | | | 1 | | | | | | | | 0 | | | | | | | | 0|1|2|3|4|5|6|7 white, it
is your move Enter your move x,y format:2,3 7 | | | | | | | | 6 | | | | | | |
| 5 | | | | | | | | 4 | | | |w|b| | | 3 | | |w|w|w| | | 2 | | | | | | | | 1 |
| | | | | | | 0 | | | | | | | | 0|1|2|3|4|5|6|7 black, it is your move Enter
your move x,y format: ` And so on. It doesn't do much beyond that - win/loss
conditions aren't setup and it doesn't digest bad input very well, but it's a
work in progress. You can comment on this post or email phil [at] philwade.org
and let me know what you think.

  
In things I actually did today: Adding code highlighting to blog posts proved
a much harder task than the 150 django snippets utilizing pygments would lead
someone to believe. I ended up using [this
guy](http://www.djangosnippets.org/snippets/822/), mainly because it provides
css style support right out of the box. The styles aren't quite what I had
dreamed of, but they're nice enough for government work.

  
I also got a chance to put the debug toolbar in place, and it is slick as hell
- I'm not sure why it isn't included in Django core. Symfony includes their
own debug bar in the default install, and based on what I'm seeing so far from
the toolbar, django should be making developers aware of the amount of
database legwork pages require. If this blog actually got any traffic, I would
have to worry about caching pretty soon. As a side note, every python package
install option I've had to deal with so far (setup.py and easy_install) is
just awesome. Not allowing developers the chance to place library code in the
wrong place is a good move. I'm a big fan of anything that makes it harder to
be stupid, for my sake and for the sake of anyone else that has to deal with
my code.

  

