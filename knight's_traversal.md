This week marked the internet's main protests against both SOPA and PIPA (look
em up!), with many websites going black on Wednesday. I did my part and
attended the protest in Manhattan, along with some co-workers. I must say,
I've never seen so many iPads, laptops and smartphones at a protest. Then
again, it's been a while since I've been to one.

  
Anyway, today I thought I'd share my solution to a programming problem I saw
over a [Programming Praxis](http://programmingpraxis.com/2012/01/20/knights-
on-a-keypad/). The blog itself gives you little programming problems, similar
to what you might encounter during a job interview. I read most of them, but
only do the occasional one.

  
This particular problem is a knight's traversal of a phone keypad. That is a
chess Knight, given a keypad like so:

1 2 3

4 5 6

7 8 9

&nbsp_place_holder;&nbsp_place_holder; 0

We are supposed to find the number of ways the knight can traverse the keypad
in _n_ steps, starting on the digit 1. For example, in two steps (counting the
initial one as a step), the knight can go to six and to eight, giving two
different paths. Here is the code:

` import sys route = { '1' : [6, 8], '2' : [7, 9], '3' : [4, 8], '4' : [0, 3,
9], #'5' : None, #we don't ever get to five '6' : [7, 1, 0], '7' : [6, 2], '8'
: [3, 1], '9' : [4, 2], '0' : [4, 6], } def knight(start, n): sum = 0 if n ==
1: return 1 else: for i in route[str(start)]: sum += knight(i, n - 1) return
sum if __name__ == "__main__": print knight(1, int(sys.argv[1])) ` (you can
also grab this code from [my bitbucket if you'd
like](https://bitbucket.org/pivotal/random-
bits/src/f245ee1ac0bd/knight_keypad.py))

  
The solution I've got is the simplest recursive solution. I hard coded the
places the knight can go from each number, mostly because the number of
destinations is short enough to type out, but also because trying to find
where the knight can move on the irregular board is a bit of a programming
puzzle in and of itself.

  
We want to find the number of end points, which is the same as the number of
paths, so the base case for our recursion is when _n_ reaches one, at which
point we return the value one. The recursive case simply sums up all of the
base cases.

  
If you look at the solutions on Programming Praxis, this one is considered the
lesser solution because things grow exponentially. Here's some timing:

  
` [phil@philsmacbook:random-bits ]$ time python knight_keypad.py 10 1424 real
0m0.046s user 0m0.014s sys 0m0.009s [phil@philsmacbook:random-bits ]$ time
python knight_keypad.py 20 5604352 real 0m6.426s user 0m6.404s sys 0m0.011s `

  
The alternative given is using a matrix to calculate the values. I haven't
attempted this yet, mostly because reading the Lisp it is written in is giving
me trouble. It probably would be a good exercise though. Maybe for next week.

