Hey.

  
So remember a week ago, when I wrote a bit about some code I had written to
solve the Knight's Keypad Traversal problem over at [Programming
Praxis](http://programmingpraxis.com/2012/01/20/knights-on-a-keypad/)? Sure
you do. It's the last post I wrote. Go read it if you haven't.

  
Anyway, my solution used recursion, and was not the best solution because the
complexity of getting the answer grew exponentially. I did not understand
fully the better solution, so this week, I made it my business to understand
it. I also decided it would be a good time to try and write some code in Ruby,
for reasons which are clear to no one. (Notes on Ruby: Arrays seem far too
difficult to create.)

  
The correct solution is the Dynamic Programming solution, which basically
means we collapse the problem into smaller subproblems that are faster to
solve. Bear with me here, as I've just finished grappling with this solution
myself. I personally got a lot out of [this stackoverflow
answer](http://stackoverflow.com/questions/2893470/generate-10-digit-number-
using-a-phone-keypad/2893570#2893570). Like the recursive solution, we find
the base case, which for this problem is the length of a single step path, and
we solve it for every position on the key pad. By adding those single step
path values together, we can determine the length of a two step path. When you
start on one and step to either six or eight, you have one step left, and the
know the length of a one step path from any number already, so you just add
those together.

i.e. [two step path from one] = [one step path from 8] + [one step path from
6].

Here is a chart that illustrates the first two rows:

  
` **1 2 3 4 5 6 7 8 9 0**

**1** 1 1 1 1 1 1 1 1 1   
**2** 2 2 2 3 3 2 2 2 2   
`

  
What makes this faster than the recursive solution is that we build up from
the base case and each successive case is just a bit of quick addition with
the previous steps answers. Here is some code.

  
` paths = [ [4, 6], #0 [6,8], #1 [7,9], #2 [4,8], #3 [0, 3, 9], #4 [], #5 [7,
1, 0], #6 [6,2], #7 [3,1], #8 [4,2] #9 ] n = ARGV[0].to_i counts = Array.new(n
+ 1) { Array.new(10) { |i| i } } (0..9).each do |i| counts[1][i] = 1 end
(2..n).each do |number| (0..9).each do |digit| sum = 0 paths[digit].each do
|from| sum += counts[number - 1][from] end counts[number][digit] = sum end end
puts counts[n][1] ` [(on bitbucket)](https://bitbucket.org/pivotal/random-
bits/src/80113fd8bc12/knight_keypad.rb)

  
I hope that it is fairly straightforward to see. I've found Ruby easier to
read than to write so far. For every path length, we just check on step back
in our array of previous answers and add together what we find. It is also
_quite_ zippy when compared to the recursive version. One is in python, the
other ruby, so the comparison is sort of moot, but just for kicks: `
[phil@philsmacbook:random-bits ]$ time python knight_keypad.py 10 1424 real
0m0.346s user 0m0.017s sys 0m0.018s [phil@philsmacbook:random-bits ]$ time
ruby knight_keypad.rb 10 1424 real 0m0.047s user 0m0.003s sys 0m0.004s `

  
(I tried to run 100, but I think the recursive version is still going.) Pretty
cool stuff. Let me know if this post doesn't make a lot of sense... I'm still
learning to explain technical things, and since this is something it took me
the better part of a day to understand, it might not be perfectly clear.
Enjoy.

