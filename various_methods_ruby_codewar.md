
```
def sort_array(source_array)
  each_odd = source_array.select(&:odd?).sort.each
  source_array.map { |a| a.odd? ? each_odd.next : a }
end
```

####each
simply iterates over the given enumerable, running the block for each value. It discards the return value of the block, and each simply returns the original object it was called on:

[1, 2, 3].each do |i|
  i + 1
end  # => [1, 2, 3]
This is simply a nicer, more universal way of doing a traditional iterating for loop, and each is much preferred over for loops in Ruby (in fact, I don't think I've ever used a for loop in Ruby).

####map
iterates over each element, using the return value of the block to populate a new array at each respective index and return that new array:

[1, 2, 3].map do |i|
  i + 1
end  # => [2, 3, 4]

####next

next → object
Returns the next object in the enumerator, and move the internal position forward. When the position reached at the end, StopIteration is raised.

Example
```
a = [1,2,3]
e = a.to_enum
p e.next   #=> 1
p e.next   #=> 2
p e.next   #=> 3
p e.next   #raises StopIteration
Note that enumeration sequence by next does not affect other non-external enumeration methods, unless the underlying iteration methods itself has side-effect, 
```
