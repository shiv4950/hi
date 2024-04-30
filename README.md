#ass1 q1 

import pandas as pd

dataset = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\cars.csv")

dataset

dataset.shape

dataset.head(5)

random_rows=5

dataset.sample(random_rows)

dataset.info()

##q2 A

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

df = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\iris.csv")

df

sns.countplot('Species',data=df)

plt.title('Frequency of Three Species')

plt.show()

###B

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

df.hist(column='SepalLengthCm',by ='Species', bins=20,figsize=(10,6),color=['red'])

plt.suptitle("Histogram for Sepal Length for iris dataset")

plt.show()

###Q3

import pandas as pd

df= pd.DataFrame(columns=['name','salary','department'])

df.loc[0]=['sagar',250000,'computer']

df.loc[1]=['suraj',300000,'It']

df.loc[2]=['tejas',260000,'computer']

df.loc[3]=['rushi',280000,'It']

df.loc[4]=['shonali',None,None]

df.loc[5]=['sarthak',250000,'IT']

df.loc[6]=['maya',280000,'computer']

df.loc[7]=['mitali',250000,'IT']

df.loc[8]=['sahil',270000,'computer']

df.loc[9]=['nilam',250000,None]

df

df= df.dropna()

df


#ass2 Q1
#apriori algo

from mlxtend.frequent_patterns import apriori

from mlxtend.frequent_patterns import association_rules

import pandas as pd

import numpy as np

dataset = pd.read_csv(r"C:\Users\HP\Downloads\archive (3)\Groceries_dataset.csv", header=None)

records = []

for i in range(0, len(dataset)):

    records.append([str(dataset.values[i, j]) for j in range(0, len(dataset.columns))])

min_support = 0.0040

min_confidence = 0.2

min_lift = 3

min_length = 2

frequent_itemsets = apriori(records, min_support=min_support, use_colnames=True)

rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=min_confidence)

filtered_rules = rules[(rules['lift'] >= min_lift) & (rules['antecedents'].apply(lambda x: len(x)) >= min_length)]

print(filtered_rules[['antecedents', 'consequents', 'support', 'confidence']])


#ass3 q1
#decision tree classifier

from sklearn.preprocessing import LabelEncoder

from sklearn.tree import DecisionTreeClassifier

from sklearn.metrics import accuracy_score

from sklearn.model_selection import train_test_split

data = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\iris.csv")

X = data.drop('Species', axis=1)

y = data['Species']

le = LabelEncoder()

y = le.fit_transform(y)

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

clf_entropy = DecisionTreeClassifier(criterion='entropy')

clf_entropy.fit(X_train, y_train)

y_pred_entropy = clf_entropy.predict(X_test)

accuracy_entropy = accuracy_score(y_test, y_pred_entropy)

print(f"Accuracy using entropy criterion: {accuracy_entropy}")

clf_gini = DecisionTreeClassifier(criterion='gini')

clf_gini.fit(X_train, y_train)

y_pred_gini = clf_gini.predict(X_test)

accuracy_gini = accuracy_score(y_test, y_pred_gini)

print(f"Accuracy using gini index criterion: {accuracy_gini}")

df = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\user.csv")

df


#ass3 q2
#guassionNB/bernoulli/multinomial classifier

import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.naive_bayes import GaussianNB, BernoulliNB, MultinomialNB

from sklearn.metrics import accuracy_score

df = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\user.csv")


X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

gnb = GaussianNB()

bnb = BernoulliNB()

mnb = MultinomialNB()

gnb.fit(X_train, y_train)

bnb.fit(X_train, y_train)

mnb.fit(X_train, y_train)

y_pred_gnb = gnb.predict(X_test)

y_pred_bnb = bnb.predict(X_test)

y_pred_mnb = mnb.predict(X_test)

accuracy_gnb = accuracy_score(y_test, y_pred_gnb)

accuracy_bnb = accuracy_score(y_test, y_pred_bnb)

accuracy_mnb = accuracy_score(y_test, y_pred_mnb)

print(f'Accuracy of GaussianNB: {accuracy_gnb:.2f}')

print(f'Accuracy of BernoulliNB: {accuracy_bnb:.2f}')

print(f'Accuracy of MultinomialNB: {accuracy_mnb:.2f}')

import pandas as pd

df = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\Salary_Data.csv")

df

#ass 3 q3
#simple linear regression

import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.linear_model import LinearRegression

import matplotlib.pyplot as plt

df = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\Salary_Data.csv")

X  = df[['YearsExperience']]

y = df['Salary']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

plt.scatter(X_test, y_test, color='red')

plt.plot(X_test, y_pred, color='blue', linewidth=3)

plt.title('Simple Linear Regression')

plt.xlabel('Years of Experience')

plt.ylabel('Salary')

plt.show()


#ass 4 q1
#k-means clustering

import pandas as pd

import numpy as np

from sklearn.cluster import KMeans

import matplotlib.pyplot as plt


data = pd.read_csv(r"C:\Users\HP\OneDrive\Desktop\DS\income.csv")

X = data[['age','fnlwgt']]

num_clusters = 3

kmeans = KMeans(n_clusters=num_clusters, random_state=42)


plt.scatter(X['age'], X['fnlwgt'],cmap='viridis')


plt.title('K-means Clustering')

plt.xlabel('Feature 1')

plt.ylabel('Feature 2')

plt.show()
