Ugh.

  
I was planning on doing an implementation of a B-Tree this week, but instead
I've managed to contract a terrible cold and don't really feel like doing
much. Instead of a B Tree, here is another quick puzzle from [Programming
Praxis](http://programmingpraxis.com/2012/01/31/string-rotation/). Given two
strings, the code must determine if the second is a rotation of the first. For
example "ttes" and "stte" are rotations of "test". Here is a bit of code:

  
` def rotate_eq(string1, string2): if len(string1) != len(string2): return
False start = string1[0] length = len(string1) match = False for i in range(0,
length): if string2[i] == start: match = True for j in range(i, length + i):
#print "does ", string2[j % length], " equal ", string1[j - i] if string2[j %
length] != string1[j - i]: match = False break `

  
First, the strings must be the same length. After that, I search for first
letter of the original string in the second. It then cycles through the rest
of the string using offsets and modulus to properly rotate through the strings
and compare every character.

  
After solving it the hard way, I looked at the given solution. It turns out if
you double up the original string, any rotation of that string is contained in
the new double version. Quite clever, and rather simple to code up:

  
` def rotate_eq2(string1, string2): if len(string1) == len(string2): temp =
string1 + string1 if string2 in temp: return True return False `

  
It makes my original version look like overkill. You live, you learn. You can
get the source [on Bitbucket](https://bitbucket.org/pivotal/random-
bits/src/96b2047260e5/string_rotation.py).

