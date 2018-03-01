# lazy

### Returns a lazy enumerator, whose methods map/collect, flat_map/collect_concat, select/find_all, reject, grep, #grep_v, zip, take, #take_while, drop, and #drop_while enumerate values only on an as-needed basis.

http://ruby-doc.org/core-2.5.0/Enumerable.html#method-i-lazy
http://patshaughnessy.net/2013/4/3/ruby-2-0-works-hard-so-you-can-be-lazy


```
require 'prime'

def gap(g, m, n)
  # find prime numbers between (m...n) and collect them in an array
  # find a pair of consecutive prime numbers that has a gap of g and return array[s] of the pair(s)
  (m..n).lazy.select (:&.prime?).each_cons(2).find { |a,b| (b - a) == g }
end
```

So rather than do *all* the work at once, it works on _one_ element at a time.

So your code without `lazy`
finds all the primes
then it takes them two at a time
then it finds the first one with a gap
With lazy
it works each number one at a time
Then it sees the `each_cons(2)` so it gets two primes at a time
and checks them.
Essentially your code does this:
3, 5, 7, 11, 13, …. Now lets take them two at a time and then find a gap
with lazy it does
`3, 5`, is that a gap?
`5, 7` is that a gap?
`7, 11` is that a gap?
And *STOPS* when it finds the first one
It will _not_ generate the full list of primes.
It only generates enough until your `find` says “ok, I can stop now, I found what I need”
