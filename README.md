from mlxtend.frequent_patterns import apriori
from mlxtend.frequent_patterns import association_rules
import pandas as pd
import numpy as np

# Load the dataset
dataset = pd.read_csv(r"C:\Users\HP\Downloads\archive (3)\Groceries_dataset.csv", header=None)

# Convert the dataset to a list of lists
records = []
for i in range(0, len(dataset)):
    records.append([str(dataset.values[i, j]) for j in range(0, len(dataset.columns))])

# Apply Apriori algorithm
min_support = 0.0040
min_confidence = 0.2
min_lift = 3
min_length = 2

frequent_itemsets = apriori(records, min_support=min_support, use_colnames=True)
rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=min_confidence)

# Filter rules based on lift and length
filtered_rules = rules[(rules['lift'] >= min_lift) & (rules['antecedents'].apply(lambda x: len(x)) >= min_length)]

# Display Support and Confidence of each rule
print(filtered_rules[['antecedents', 'consequents', 'support', 'confidence']])
 
