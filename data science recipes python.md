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
max(dic, key=dic.get)
# or
max(dic.keys(), key=lambda k: dic[k])

# Count the number of each item in an iterable.  Create a key->count dictionary.
collections.Counter(iterable)

# flatmap
# TODO: use itertools.chain or something so it's not forced to be a list
def flatmap(f, items):
  return chain.from_iterable(imap(f, items))

# flatten a list of lists into a single list
list(itertools.chain(*list_of_lists))

# accumulate (partial sums) (partial applications of a chain of binary operations)
partial_sums = itertools.accumulate(nums)
partials = itertools.accumulate(list_, func=my_binary_op)

# reduce (like accumulate, but only returns the final value)
the_sum = functools.reduce(int.__add__, nums)

# apply a binary function / binary operation to two Pandas Series `a` and `b`
pd.DataFrame({'a': a, 'b': b}).fillna(my_fill_value).apply(lambda r: my_binary_op(r[0], r[1]), axis=1)

# Pandas DataFrame group by and aggregate
agg_config = {keys are column names and values are aggregation names such as 'sum'}
df_agg = df.groupby([group_by_col], as_index=False).agg(agg_config)

# Pandas Series filter by index / key
series.filter(keys_to_keep)

# Get the number of rows of a pandas dataframe len df
num_rows = len(df.index)
