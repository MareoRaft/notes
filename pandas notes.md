df
df.head()
df[df['year'] == 1880]

df.groupby('year')
df.groupby('year').size()
df.groupby(['year', 'sex']).size()
# returns a Series where index is hierarchical on (year, sex), and values are size of each group



