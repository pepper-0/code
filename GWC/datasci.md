# Data Sci + AI

<aside>
🗒️

Intro to Responsible AI

- TRAFFIC framework
    - Transparency
    - Reliability
    - Accountability
    - Fairness (in treatment)
    - Fairness (in access)
    - Inclusiveness
    - Confidentiality
- AI response patterns
    - Let's look at the first major pattern: Technical Deflection. This is when someone responds to concerns by emphasizing the AI's technical superiority, without addressing the actual impacts. You might hear things like:
    - The second major pattern is Impact Minimization. This pattern downplays or dismisses potential problems instead of addressing them. Common responses include:
</aside>

<aside>
📝

Intro to Data Sci

- Define, Collect, Clean, Analyze, Interpret, Apply
- pandas
- matplotlib

```python
import pandas as pd

# reading from a csv file, data frame
movieData = pd.read_csv('./rotten_tomatoes_movies.csv')

# methods to interpret/read data:
print(movieData.head()) # gives first 5 entries
print(movieData[num]) # gives the entries within that category (think like it's
											# a 2D array, that you're choosing which column to display
favMovieBooleanList = movieData["movie_title"] == favMovie # this filters 
											# through all them and assigns a bool to see if 
											# matches up
											
favMovieData = movieData.loc[favMovieBooleanList] # locates movie data and by passing
											# in a boolean list, it filters until it encounters one 
											# that's true 
	#favMovieData is a Pandas Series object. it's a 'single-column slice' of the DF
										
# similar, but using diff. conditional
animationMovieBooleanList = movieData["genres"].str.contains("Animation") # same
											# as java's contains. you use .str to indicate it's a str
											# because python dum dum ig. 
											# this is filtering and assigning booleans as it goes thru
											# to its own list
animationMovieData = movieData.loc[animationMovieBooleanList] # filtering in proper

# find attributes of (filtered) df
animationMovieData.shape # returns tuple w/ (number_of_rows, number_of_columns)
												 # add brackets to index which num you want specifically
												 
minRating = animationMovieData["audience_rating"].min() # find min
maxRating = animationMovieData["audience_rating"].max() # find max
mean = animationMovieData["audience_rating"].mean() # find mean
median = animationMovieData["audience_rating"].median()

# find attributes of (filtered) pandas series
numOfMovies=animationMovieData.shape[0] # takes tuple of 'shape' of 
												# and takes the first value (rows)
```

- matplotlib

```python
import matplotlib.pyplot as plt

# create a graph
plt.hist(animationMovieData["audience_rating"]) # histograph
										# includes passed in data of ratings of animation movies
										# "audience_rating" is given to be as the x-axis
plt.scatter(data = animationMovieData, x = "audience_rating", y = "critic_rating")
										# this provides us more ctrl over how 
										# the graph appears (what's x, what's y) 
										# in a very general object

	# finetuning a histograph
plt.hist(animationMovieData["audience_rating"], range = (0, 100), bins = 20] 
										# the x axis is being set from 0-100
										# bins = how many separate bars 

# add labels and adjustments
plt.grid(True) # yes it has a grid
plt.title("") # has a title
plt.xlabel("")
plt.ylabel("") # has 

```

</aside>

<aside>
📝

Data Science for Good

- data story: hypothesis of data, research question

> attributes of data:
> 
> - dataset size (too small or too large?)
> - specificity
> - format

> CARPS: **dataset quality**
> 
> - C: currency
> - A: authority
>     - credentials of author
> - R: relevance
>     - cherry-picking data
> - P: purpose

```python
# pandas 
import pandas as pd
import GWCutilities as util

lwd.columns # prints only first and last 10 column labels

util.vformat_list(lwd.columns) # using GWC's thing to make it into a fully printed list

# plotting graph
plt.hist(x='year', data=lwd, edgecolor='white', bins=29)
				# specifies that you can pass it in in which spots, same as 
				# the plotting the scattergram

# methods
listOfCountries = lwd["country_name"].unique() #sorts and only retains one of 
				# each unique entry in the column

# step 2 code (used prior)
oneCountryBooleanList = lwd["country_name"] == "Vietnam" # we did this
				# in course 2 as well, it converted it into boolean
				# list based on whether its country name == Vietnam. 
				# if so, then yay. and it'll become true
oneCountryData = lwd.loc[oneCountryBooleanList] # if it's true, then 
				# store that in there as well
	
	
# step 3: between method
pandas.Series.between(low, high) # selecting data

# step 4: ylim method
plt.ylim(low, high) # selecting the y range 
	
	# remember:
		# include ALL data from all time frame, not just a snippet (or vice versa, not time frame but number
		# discern correlation vs. causation
```

> data story components:
> 
> - setting
> - characters
> - context
> - solution
</aside>

<aside>
📝

Intro to Machine Learning

> features of ML (classification ML)
> 
> - features (observed characteristics that AI uses to make prediction
> - classification model
> - classes
- machine learning: the ways systems ID patterns, make decisions, and improve themselves w/ data
    - decision tree classifiers
        - node = a point
        - splitter = the separation at a node
    - ML vs conditionals: we don’t tell the decision tree how to split; it learns how to categorize by itself
    - gini impurity index: measure of how often a data point is mislabeled; the ML wants to prevent it from occuring

steps to creating a model

1. obtain data
2. encode: translating data into numbers, as 
    - label encoding: assigning unique values an int
        - used when there are only 2 poss. values, or there are multiple vals with implied order
            - ex: 0: fair, 2: very good: 3: excellent
    - one hot encoding: using 0 and 1 for T/F for each unique val
        - used when one column represents independent categories
            - ex: white: 0, black: 0, hispanic: 1, asian: 0

```python
import pandas as pd
import GWCutilities as util

# encoding: first param is df, second param is list with all columns to encode
# label encoder

df = util.labelEncoder(df, ["HeartDisease", "GenHealth"]) # this is telling
										# util to call the label encoding function to be done
										# for the HeartDisease and GenHealth categories.
print(df.head()))

# one hot encoder
df = util.oneHotEncoder(df, ["Race])
```

1. divide dataset
    1. split dataset into 1) training (~80%) 2) testing (~20%)
    2. train model with training
    3. testing model with testing
    - split dataset to confirm it’s not memorizing, it’s learning patterns
    
    > use scikit-learn
    > 

```python
# library is from scikit-learn (aka sklearn)
from sklearn.model_selection import train_test_split

# hold features (aka the entire dataset, minus the "HeartDisease" column
# axis = 1 means you're dropping a column, not a row
X = df.drop("HeartDisease", axis = 1) 
# holds target class, the HeartDisease column that you're determining
Y = df["HeartDisease"]

# assigning 4 variables at a time:
	# X_train: the features that the model will be trained on
	# X_test: the features that the model will be testing with
	# y_train: the labels the model will be given for training
	# y_test: the labels that the model uses for test examples
	
	# adding random_state parameter (optional) and assigning an int will
		# ensure the decision tree will always be the exact same each time
		# you run the program
X_train, X_test, y_train, y_test = train_test_split(X, y. random_state = 1)
```

1. train dataset

```python
from sklearn.tree import DecisionTreeClassifier

# creates decision tree classifier
	# adjust the depth param to adjust the "depth" of nodes in dec tree
	# you can use "None" instead if you want to extend the dec tree as much
	# 
		
clf = DecisionTreeClassifier(max_depth = 3)
	# this is the data youre feeding it 
clf = clf.fit(X_train, y_train)
```

1. measure accuracy based on test data

```python
# giving it some test x's, it's now giving us what it thinks
test_predictions = clf.predict(X_test) 

from sklearn.metrics import accuracy_score

# based on the clf model it js made, see how accurate its predictions were
test_acc = accuracy_score(y_test, test_predictions)

# prints out the decision tree created, passing in X.columns to tell it to label
# the nodes
util.printTree(clf, X.columns)

from sklearn.metrics import confusion_matrix

# creating a confusion matrix giving test results vs predictions, and labels
# formats it a little better
cm = confusion_matrix(y_test, test_predictions, labels = [1,0])
```

![image.png](image.png)

- overfitting: the model memorizes training data so well, that the model can’t perform well on new data
1. let tree reflect on performance
- to see if it’s overfitting: compare training accuracy score vs. testing accuracy score
    - it’s based on how similar these two scores are
- max_depth adjustments can help fix accuracy; less depth may make the prerquisites for determining it to be more broad, thus helping with increasing the

```python

```

</aside>

<aside>
📝

Basic Neural Nets

> **Steps to create neural net**
> 
> 1. acquire data
> 2. construct neural net model
> 3. train model
> 4. evaluate model
- different from making classification tree, because you construct a model, then train it instead of it creating the model as its being trained.
- eval = is it good enough?
- accuracy score: % it got right

> ways to improve model:
> 
> - model insights (how do we measure a model?)
> - model buildlng (what are neural nets? how can we improve the model?)
> - data exploration (learn more about the data)
>     - here in our class, we have a df with a column of its class, and 784 (28x28) columns with its color stored
>     - imbalance in dataset’s classes: may create bias
>         - more balanced = usually fairer

</aside>

![image.png](image%201.png)

![image.png](image%202.png)