To me, python's greatest strength is that the syntax is almost identical to
the form that programs take when they appear in your mind. This makes the time
from the initial thought to final code shorter, and makes it easy for others
reading your code to understand your thinking. This makes it ideal for
interview problems, but mostly just makes it a joy to work with.

  
To profile some code that I had written, I was calculating the average of many
page loads. My inital approach was to write down the numbers and then plug
them into a calculator. Simple enough, but like most pure programming
problems, very boring for numbers greater than three or four. Sounds like a
good time for some python.

  
To start, I formatted my numbers as simply as possible. The file looked like
this:

  
` Baseline Wall 130 45 300 312 60 77 CPU 100 50 330 300 60 78 Mem 2000 2121
400 3100 1945 1224 `

  
I wanted it to print out the name of the run (Baseline in this case), and then
print an average of each measurement. The code I wrote was this:

  
` f = open('runs', 'r') for line in f: parts = line.split(' ') sum = 0 count =
0 for part in parts: try: n = int(part) sum += n count += 1 except ValueError:
print part try: print sum / count except ZeroDivisionError: pass `

  
Short, and gets the job done. The best part is that it only took about five
minutes from inception to working code. I needed to run it twice to get the
names of the exceptions correct, but beyond that, it took me almost no time
compared to the amount of time it saved, and that's a beautiful thing.

  
Could I have done it with awk? or excel? Certainly. However, one requires
opening up excel (if you even have it. Also, yuck), and the other would
require a bit of reading to figure out. Neither is really ideal. Although the
awk one might be sort of fun. Perhaps we'll see about that in a future post.

