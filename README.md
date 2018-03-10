
# Instant Data Science

When starting any course, you likely look at the syllabus to see what's covered and answer can you do it.  In this lesson, we'll hope to give you a sense of how with just a little bit of knowledge you can make some real progress in using programs to answer questions with data.  

To do so, we'll have lessons and labs on the following topics: 
* strings
* variables
* lists
* dictionaries
* loops and iteration
* data visualization
* functions


So this first section will go into seven topics, with lessons and labs on each. There we will break down the content down step by step.  But this lesson is about instant data science.  So here is a whirlwind tour of what through these first topics.

### Song Analysis

What makes a hit record?  Does repetitiveness help, like a lullabye?  And is our music getting more repetitive over time?  Questions like these were asked by the great computer scientist Donald Knuth in 1977, and were reasked and answered, by Colin Morris in [this article](https://pudding.cool/2017/05/song-repetition/).

Here is a chart that he produced showing some of the most repetitive popular artists.  How was something like this made and calculated?

![](./song-chart.png)

### Analyzing one song

Let's take the song Barbara Ann, the most repetitive song of the Beach Boys, and remastered by the cast of Saved by the Bell.  

![](./saved-by-bell.gif)

Here are the some of the lyrics.

    Ah, ba ba ba ba Barbara Ann
    Ba ba ba ba Barbara Ann

    Oh Barbara Ann, take my hand
    Barbara Ann
    You got me rockin' and a-rollin'
    Rockin' and a-reelin'
    Barbara Ann ba ba
    Ba Barbara Ann

    Went to a dance, lookin' for romance
    Saw Barbara Ann, so I thought I'd take a chance
    With Barbara Ann, Barbara Ann
    Take my hand
    You got me rockin' and a-rollin'
    (Oh! Oh!)
    Rockin' and a-reelin'
    Barbara Ann ba ba
    Ba ba ba ba black sheep

    Ba ba ba ba Barbara Ann
    Ba ba ba ba Barbara Ann

It keeps going, but you get the point.  Now let's say that we wanted to count up how many times each word in the above selection appears.  Without a computer, we could do the following: 

* Place each of the words on a separate index card
* Allocate space for a small pile for each unique word
* Then, go through the index cards one by one
* And for each index card, increase the size of it's related pile by one

Ok, now that we have a plan, let's translate this into code.

### Working with Strings and Variables

In code we do something similar.  First we place our pile of words, into a string, which is a data structure that just represents text.


```python
"Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann"
```




    "Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann"



To place have this be a string in Python, notice that we place quotes at the start and end of text.  If we don't do this, Python will give us an error.


```python
Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann
```


      File "<ipython-input-61-5fbb40878925>", line 1
        Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann
                ^
    SyntaxError: invalid syntax



Ok, so we need the quotes for a string, but to hold onto this string and reference it later, we assign it to a variable.  


```python
lyrics = "Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann"
```

Now whenever we type the word lyrics into Python we can see our string.


```python
lyrics
```

Ok, so strings are great for performing operations on text. For example we can call a method `title` on a string to capitaize the first letter of each word.


```python
lyrics.title()
```

The uniformity here is good.  After all, eventually, we want to place the lowercased "ba" and the uppercased "Ba" in the same pile, so let's just make them the same.  We can accomplish this by setting `lyrics.title()` equal to a new variable `titled_lyrics`.


```python
titled_lyrics = lyrics.title()
titled_lyrics
```




    "Ah, Ba Ba Ba Ba Barbara Ann Ba Ba Ba Ba Barbara Ann Oh Barbara Ann, Take My Hand Barbara Ann You Got Me Rockin' And A-Rollin' Rockin' And A-Reelin' Barbara Ann Ba Ba Ba Barbara Ann Went To A Dance, Lookin' For Romance Saw Barbara Ann, So I Thought I'D Take A Chance With Barbara Ann, Barbara Ann Take My Hand You Got Me Rockin' And A-Rollin' (Oh! Oh!) Rockin' And A-Reelin' Barbara Ann Ba Ba Ba Ba Ba Ba Black Sheep Ba Ba Ba Ba Barbara Ann Ba Ba Ba Ba Barbara Ann"



Not bad, strings are great at manipulating all of our text at once.  However, strings **are not** good for thinking about each word as a separate entity.  For that we should use a list.

### Lists in Python 

So to think of our text as having separate words need to transform this continuous string into a list of words.  We can tell our computer to do this.  But speak on it's level, think of the computer as a small child who works really fast.  So tell it, "Go through each character in the string, and when you see a space, split the string into a new string".  Here is those directions in code.


```python
list_of_lyrics = titled_lyrics.split(' ')
```

We store the result to a variable.  Do you want to see what it looks like?  Ok, but be prepared for a lot of words.  Just scroll through them, and we'll meet up afterwards.


```python
list_of_lyrics
```




    ['Ah,',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Barbara',
     'Ann',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Barbara',
     'Ann',
     'Oh',
     'Barbara',
     'Ann,',
     'Take',
     'My',
     'Hand',
     'Barbara',
     'Ann',
     'You',
     'Got',
     'Me',
     "Rockin'",
     'And',
     "A-Rollin'",
     "Rockin'",
     'And',
     "A-Reelin'",
     'Barbara',
     'Ann',
     'Ba',
     'Ba',
     'Ba',
     'Barbara',
     'Ann',
     'Went',
     'To',
     'A',
     'Dance,',
     "Lookin'",
     'For',
     'Romance',
     'Saw',
     'Barbara',
     'Ann,',
     'So',
     'I',
     'Thought',
     "I'D",
     'Take',
     'A',
     'Chance',
     'With',
     'Barbara',
     'Ann,',
     'Barbara',
     'Ann',
     'Take',
     'My',
     'Hand',
     'You',
     'Got',
     'Me',
     "Rockin'",
     'And',
     "A-Rollin'",
     '(Oh!',
     'Oh!)',
     "Rockin'",
     'And',
     "A-Reelin'",
     'Barbara',
     'Ann',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Black',
     'Sheep',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Barbara',
     'Ann',
     'Ba',
     'Ba',
     'Ba',
     'Ba',
     'Barbara',
     'Ann']



Ok, so this is a list.  It's an ordered collection, and as you can see we are now treating each word as an individual entity.  Each individual entity of a list is called an element.  How many elements are there in this list?


```python
len(list_of_lyrics)
```

Ok, but what about unique words. Let's see a list of all of the unique words of the list?


```python
unique_words = set(list_of_lyrics)
```


```python
unique_words
```

Ok, now we can see that our unique words is significantly smaller than our total list of words.  How much smaller?


```python
len(unique_words)
```

A lot.

So there's a lot of repetition here.  It's time to keep track of each word and the number of occurrences of each word.

### Using dictionaries

So we can imagine presenting this data almost as a table.  A word to the left and the number of occurrences to the right.  

| Word        | Count           |
| ------------- |:-------------:|
| Ann     | 2 |
| Barbara     | 3 |
| Ba     | 8 |

In Python, this looks like a dictionary.


```python
word_counts =  {'Ann': 2, 'Barbara': 3, 'Ba': 8}
```

A dictionary is a collection of key value pairs, and use them to store associated data.  Here, each word is associated with it's count. And we can use the key to access the associated value.


```python
word_counts['Ann']
```

And also use the key to reassign that value.


```python
word_counts['Ann'] = 33
```


```python
word_counts
```

So that's the form we want.  How do we get there from our `list_of_lyrics` or the unique words in there?

Well we can start by having our dictionary have each key be a separate word, and then set the corresponding value to zero.  Kind of like making an empty category for each of our words.  Then we would be ready to set the number for each of the words.

Let's start with a dictionary that has a key for each unique word and each value starting at the number zero.  We can create a new dictionary and set the keys to `unique_words` and the values all to `0` with the `fromkeys` method.  We call this a `word_histogram`.


```python
word_histogram = dict.fromkeys(unique_words, 0)
word_histogram
```




    {'(Oh!': 0,
     'A': 0,
     "A-Reelin'": 0,
     "A-Rollin'": 0,
     'Ah,': 0,
     'And': 0,
     'Ann': 0,
     'Ann,': 0,
     'Ba': 0,
     'Barbara': 0,
     'Black': 0,
     'Chance': 0,
     'Dance,': 0,
     'For': 0,
     'Got': 0,
     'Hand': 0,
     'I': 0,
     "I'D": 0,
     "Lookin'": 0,
     'Me': 0,
     'My': 0,
     'Oh': 0,
     'Oh!)': 0,
     "Rockin'": 0,
     'Romance': 0,
     'Saw': 0,
     'Sheep': 0,
     'So': 0,
     'Take': 0,
     'Thought': 0,
     'To': 0,
     'Went': 0,
     'With': 0,
     'You': 0}



### Loops

Ok, that we have two nice data structures, a `list_of_words` to start with, and a `word_histogram` to end with, we are ready to proceed.  Remember the plan that we stated we could use to count up how many times each word appears:

* Place each of the words on a separate index card
* Allocate space for a small pile for each unique word
* Then, go through the index cards one by one
* And for each index card, increase the size of it's related pile by one


So we already have each of our words on a separate index card.  That is our `list_of_lyrics`.  We have also allocated space for a small pile for each unique word, that is our `word_histogram`.  So all that's left are the last two steps.

In Python to go through elements of a list one by one, we use a for loop.


```python
for number in [1,2,3,4]:
    print(number + 10)
```

    11
    12
    13
    14


Ok, so now here what we want to do is go through the elements of our `list_of_lyrics` one by one.  For each word, we want to find the related key in the dictionary and increase the value by one.  So this is what we want to do for each word: 


```python
word_histogram = dict.fromkeys(unique_words, 0)
word = 'Barbara'
word_histogram[word] # 0 
# line 5 below is especially confusing, we'll cover it in detail later
word_histogram[word]  = word_histogram[word]+ 1 
word_histogram['Barbara'] # 1
```




    1



Now combining this with the `for` loop we have the following.


```python
word_histogram = dict.fromkeys(unique_words, 0)
for word in list_of_lyrics:
    word_histogram[word]  = word_histogram[word]+ 1 
```


```python
word_histogram
```




    {'(Oh!': 1,
     'A': 2,
     "A-Reelin'": 2,
     "A-Rollin'": 2,
     'Ah,': 1,
     'And': 4,
     'Ann': 9,
     'Ann,': 3,
     'Ba': 25,
     'Barbara': 12,
     'Black': 1,
     'Chance': 1,
     'Dance,': 1,
     'For': 1,
     'Got': 2,
     'Hand': 2,
     'I': 1,
     "I'D": 1,
     "Lookin'": 1,
     'Me': 2,
     'My': 2,
     'Oh': 1,
     'Oh!)': 1,
     "Rockin'": 4,
     'Romance': 1,
     'Saw': 1,
     'Sheep': 1,
     'So': 1,
     'Take': 3,
     'Thought': 1,
     'To': 1,
     'Went': 1,
     'With': 1,
     'You': 2}



Ok, that's it.  If we want to see how many time 'Rockin' appears, we easily can.


```python
word_histogram["Rockin'"]
```




    4



### Visualizing the data

We've got our answer in code.  The final step is to turn it into a chart.  We'll use a library -- which is a collection of code we get from the Internet that does not come with Python -- called Plotly to make our charts. 

In the first four lines we tell Python to get ready to use this library.  And in the last line we tell Python to plot our `trace`.

The meat of the code, the part that we will be changing, is our `trace`.  Trace points to a dictionary with a key of `x` that points to a list of x_values, and a key of `y` that points to y_values.  And a `type` to indicate that this will be a bar chart.


```python
import plotly
from plotly.offline import iplot, init_notebook_mode
from plotly import tools
import plotly.graph_objs as go
init_notebook_mode(connected=True)


trace = {
 'type': 'bar',
 'x': ['Barbara', 'Ann'],
 'y': [12, 3]}
plotly.offline.iplot({'data': [trace]})
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<div id="eaf061e3-06fe-4a0f-88ff-4bc2ab44b4ab" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("eaf061e3-06fe-4a0f-88ff-4bc2ab44b4ab", [{"type": "bar", "x": ["Barbara", "Ann"], "y": [12, 3]}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>



```python
trace
```




    {'type': 'bar', 'x': ['Barbara', 'Ann'], 'y': [12, 3]}



You can see that x values  point to an array of the x values, our list of words, and `y` points to an array of y values, the number of times each word appears.  So lets set `x` and `y` equal to those values.


```python
unique_words
```




    {'(Oh!',
     'A',
     "A-Reelin'",
     "A-Rollin'",
     'Ah,',
     'And',
     'Ann',
     'Ann,',
     'Ba',
     'Barbara',
     'Black',
     'Chance',
     'Dance,',
     'For',
     'Got',
     'Hand',
     'I',
     "I'D",
     "Lookin'",
     'Me',
     'My',
     'Oh',
     'Oh!)',
     "Rockin'",
     'Romance',
     'Saw',
     'Sheep',
     'So',
     'Take',
     'Thought',
     'To',
     'Went',
     'With',
     'You'}




```python
trace = {'type': 'bar', 'x': unique_words, 'y': list(word_histogram.values())}
```


```python
import plotly
from plotly.offline import iplot, init_notebook_mode
from plotly import tools
import plotly.graph_objs as go
init_notebook_mode(connected=True)

trace = {'type': 'bar', 'x': list(unique_words), 'y': list(word_histogram.values())}
plotly.offline.iplot({'data': [trace]})
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<div id="d0ae0710-b046-4232-8654-aed4ae8383b6" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("d0ae0710-b046-4232-8654-aed4ae8383b6", [{"type": "bar", "x": ["You", "Went", "With", "Barbara", "Take", "Dance,", "Sheep", "A-Reelin'", "Oh!)", "So", "Rockin'", "Oh", "For", "Black", "Hand", "Me", "And", "Ah,", "Romance", "To", "Ba", "Ann,", "Got", "(Oh!", "Ann", "Lookin'", "A-Rollin'", "Chance", "A", "Saw", "I", "I'D", "My", "Thought"], "y": [2, 1, 1, 12, 3, 1, 1, 2, 1, 1, 4, 1, 1, 1, 2, 2, 4, 1, 1, 1, 25, 3, 2, 1, 9, 1, 2, 1, 2, 1, 1, 1, 2, 1]}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


And now we have plotted our words. The beach saying "Ba" 25 times, and remember we only copied over some of the lyrics.  Repetitive indeed.

### Summary

In the first twenty lessons, we will cover these topics and more.  Hopefully, in this section you can see that even with just a bit of knowledge you can really put code to use.  It may have seemed like a lot of work, but the work was in the learning, not the code.  

All of the code was just a ten lines.


```python
lyrics = "Ah, ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann Oh Barbara Ann, take my hand Barbara Ann You got me rockin' and a-rollin' Rockin' and a-reelin' Barbara Ann ba ba Ba Barbara Ann Went to a dance, lookin' for romance Saw Barbara Ann, so I thought I'd take a chance With Barbara Ann, Barbara Ann Take my hand You got me rockin' and a-rollin' (Oh! Oh!) Rockin' and a-reelin' Barbara Ann ba ba Ba ba ba ba black sheep Ba ba ba ba Barbara Ann Ba ba ba ba Barbara Ann"
titled_lyrics = lyrics.title()


list_of_lyrics = titled_lyrics.split(' ')
unique_words = set(list_of_lyrics)
word_histogram = dict.fromkeys(unique_words, 0)

for word in list_of_lyrics:
    word_histogram[word] = word_histogram[word] + 1
```

And another 8 lines to plot.


```python
import plotly
from plotly.offline import iplot, init_notebook_mode
from plotly import tools
import plotly.graph_objs as go
init_notebook_mode(connected=True)

trace = {'type': 'bar', 'x': list(unique_words), 'y': list(word_histogram.values())}
plotly.offline.iplot({'data': [trace]})
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<div id="5d37d4d3-5a2a-40f7-ad48-74847bc6aa77" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("5d37d4d3-5a2a-40f7-ad48-74847bc6aa77", [{"type": "bar", "x": ["You", "Went", "With", "Barbara", "Take", "Dance,", "Sheep", "A-Reelin'", "Oh!)", "So", "Rockin'", "Oh", "For", "Black", "Hand", "Me", "And", "Ah,", "Romance", "To", "Ba", "Ann,", "Got", "(Oh!", "Ann", "Lookin'", "A-Rollin'", "Chance", "A", "Saw", "I", "I'D", "My", "Thought"], "y": [2, 1, 1, 12, 3, 1, 1, 2, 1, 1, 4, 1, 1, 1, 2, 2, 4, 1, 1, 1, 25, 3, 2, 1, 9, 1, 2, 1, 2, 1, 1, 1, 2, 1]}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


These next sections will go through each of the topics above, so that we can use the tools above to answer questions with data efficiently with code.
