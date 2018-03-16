#### refactor
def count_chars(s)
 Hash[s.chars.uniq.zip s.chars.uniq.map {|a| s.count(a)}]
end

def count_chars(s)
  keys = s.chars.uniq
  value = s.chars.uniq.map {|a| s.count(a)}
  Hash[keys.zip value] 
end  
 
 
 ### Nifty little method 'zip'
 http://dfriedm.github.io/blog/2013/10/12/ruby-zip-method/
 
Converts any arguments to arrays, then merges elements of self with
corresponding elements from each argument. This generates a sequence of
self.size n-element arrays, where n is one more that the count of
arguments. If the size of any argument is less than enumObj.size, nil values
are supplied. If a block is given, it is invoked for each output array,
otherwise an array of arrays is returned.
