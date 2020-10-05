# This file strictly contains 1-line recipes for mutating data in python. imports are excluded for brevity

# Cartesian product of two iterables. Take the set of all pairs between two iterables.
itertools.product(A, B)
# or
np.outer(v1, v2)
# or
[(a, b) for a in A for b in B]

# Set choose 2 elements. Get all distinct unordered pairs from an iterable. Get all subsets of size 2.
itertools.combinations(X, 2)
# or
{{a, b} for a in X for b in X if len({a, b}) == 2}
# or
list(nx.complete_graph(X).edges())

# Sorting pairs where we descend by the first element and ascend by the second
sorted(pairs, key=lambda x: (-x[0], x[1]))[:]

# Getting the item with the maximum value out of a dictionary
max(dic.items(), key=lambda x: x[1])

# Getting the key with the maximum value out of a dictionary
max(dic.keys(), key=lambda k: dic[k])

# Count the number of each item in an iterable.  Create a key->count dictionary.
collections.Counter(iterable)

# flatmap

# accumulate (partial sums) (partial applications of a chain of binary operations)
partial_sums = itertools.accumulate(nums)
partials = itertools.accumulate(list_, func=my_binary_op)

# reduce (like accumulate, but only returns the final value)
the_sum = functools.reduce(int.__add__, nums)

