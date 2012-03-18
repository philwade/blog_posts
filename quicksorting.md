I've spent a bit of time this week thinking about
[QuickSort](http://en.wikipedia.org/wiki/Quicksort). More specifically, I've
been thinking about the complexity of the Quicksort worst case. On an already
sorted set, Quicksort has a complexity of O(n^2), which I guess I understand
on a basic level. Generally speaking, when the set is already sorted,
Quicksort needs to compare every element to every other element each time it
partitions the set. Partition n times, doing n comparisons, then you have n^2
comparisons. Makes sense, but instead of just leaving it, I've been trying to
grasp it more definetly. In my mind, the comparisons on subsequent sets should
be getting smaller. ie n-1, n-2, n-3 comparisons and so on.

  
I thought perhaps coding up a measurement of the complexity would help me wrap
my head around it.

  
` class QuickSorter: def __init__(self): self.depth = 0 self.complexity = 0
def quickSort(self, set): self.depth += 1 self.complexity += 1; if(len(set) ==
1 or len(set) == 0): return set high = [] low = [] pivot = set[0]
set.remove(pivot) for i in set: self.complexity += 2 if i > pivot:
high.append(i) else: low.append(i) return self.quickSort(low) + [pivot] +
self.quickSort(high) if __name__ == "__main__": q = QuickSorter() runset = [1,
2, 3, 4, 5, 6, 7] print q.quickSort(runset) print q.complexity `

  
After a bit of messing around trying to decide what should be part of the
complexity measurement, you'll see I decided on counting the check on the
length of the array, and the greater than and less than checks on values. It
all seemed to make perfect sense, but my numbers kept coming out wrong.

  
On an already sorted array of length 3, instead of getting back 9 operations,
I got 11. A set of 6? 41 operations. It was making me insane, but then I
realized that the actual complexity of the worst case ended up being O(n^2 +
(n - 1)). The n-1 comes from the length checks on all of the empty sets. This
promptly made me remember the way big O notation is handled, where the slowest
growing elements of the complexity are discarded. What is the growth of n-1 in
comparison to the speed of n^2? Insignificant.

  
It was a nice bonus to figure that all out, but I still don't think I'm
satisifed. The issue with n-1 should be a lesson that understanding the
complexity of these algorithms is less about actual exact measurement, and
more about mathematical understanding of the situation. So, while I think I
"get" it enough to get by, I'm going to spend a bit of time re-familiarizing
myself with the math.

  
Anyway, I put the code up [here.](https://bitbucket.org/pivotal/random-
bits/src/eaa722f0c36a/quickSort.py) There is also an implementation of the in-
place version of Quicksort there as a bonus.

  
As a quick aside, I realize that picking the first element in the array as a
pivot is bad practice, as it often triggers worst case behavior. That was my
intention here.

  
_**Update:_** I've spent a bit more time reading after writing this post, and
I've come to the following understanding of Quicksort: in the best case, we
evenly divide the array into roughly half the size, so we recursively build
log n levels before we reach our base case, a list of size one. On each level,
there is O(n) amount of work done, which gives us the case, O(n log n). By the
same token, when we encounter the worst case, we must recursively divide the
set n times before we get to the base case, giving us n levels with O(n)
complexity, coming out to the worst case O(n^2).

  
Whew. That feels much better.

