This has been quite a week. I've made the decision to take a new job and move
my fiancee and myself to Buffalo from Brooklyn. We think that moving there
will give us a better opportunity to live the lifestyle we want. A shorter
commute, more space and proximity to family are among a whole host of reasons
we've decided to do it. It was a difficult decision, and we'll both miss a lot
of things about Brooklyn, but I think its for the best, even though I feel a
little overwhelmed right now.

  
Anyway, I was poking through my work computer to see if there was any code
that I didn't want to leave behind, and I found something that played off last
week's interest in Quicksort. It was a piece of code that I had written when I
first taught myself the algorithm. And, unlike most of your old code you run
into, this was more nicely written than what I wrote [just
recently](http://philwade.org/post/quicksorting/).

` #what I wrote last week def quicksortLoop(set): if len(set) <= 1: return set
high = [] low = [] pivot = set.pop(len(set) / 2) for i in set: if i >= pivot:
high.append(i) else: low.append(i) return quicksortLoop(low) + [pivot] +
quicksortLoop(high) #what I wrote a long time ago def quicksort(list): if
len(list) <= 1: return list; pivot = list.pop(len(list) / 2) less = [i for i
in list if i < pivot] more = [i for i in list if i >= pivot] return
quicksort(less) + [pivot] + quicksort(more) `

  
Instead of looping through the set and putting values into two arrays, this
implementation uses python's list comprehensions to build the more and less
lists. I think this approach is much more elegant, yielding easier to read
code.

  
This lead me to the question of whether or not the list comprehensions
incurred a signifigant amount of overhead. To find out, I stripped away all
the parts that distiguished the two different implementations from one another
with the exception of the loop vs list comprehension pieces. Then I wrote some
code to the run the two different function through the same paces.

  
` from time import time from random import randint #function definitions here
if __name__ == "__main__": loopTimes = [] compTimes = [] for i in range(1,
1000): testSet = [randint(0, 100) for x in range(1000)] cSet = list(testSet)
loopSet = list(testSet) compTime = time() quicksortComprehension(cSet)
compTime = time() - compTime compTimes.append(compTime) loopTime = time()
quicksortLoop(loopSet) loopTime = time() - loopTime loopTimes.append(loopTime)
print "Avg with loop: ", sum(loopTimes)/1000 print "Avg with list
comprehension: ", sum(compTimes)/1000 ` What this is does is sort a thousand
lists, each containing a thousand numbers between one and one hundred, using
both sorting functions. It counts the time each function takes on each list,
and then calculates an average.

  
The results are sort of interesting. ` [snpxw@PWadeiMAC:random-bits ]$ python
quicksortTimer.py Avg with loop: 0.00623641085625 Avg with list comprehension:
0.0061008477211 ` List comprehensions beat the loop every time, which is the
opposite of what I expected. I'll speculate that the difference is either some
internal optimization python makes for list comprehensions, or the pre-
allocation of the low and high arrays in the loop version. I'm going to have
to do a bit more research about what happens inside python to figure it out.

  
Regardless, the difference is negligible. Even if the list being sorted was
five thousand times larger (that is, five million elements), the difference in
the two implementations would be about 0.5 seconds. Not really enough to
bother most people.

  
(The full code from this post is [here](https://bitbucket.org/pivotal/random-
bits/src/e7053a80d9cf/quicksortTimer.py).)

