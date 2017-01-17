# PageRank-Algorithm
Mathematics of Google Search

## A little bit of history
In the early 90s the first search engines used *text based ranking systems*.

**Problem:** May be millions of pages on the web using the searching word, and containing thousands of those words but any of them may not be the one that used most often.

**Solution:**
![alt tag](https://3.bp.blogspot.com/-3A5x_Q94B1U/Vkw51-cyPVI/AAAAAAAABAA/p9uyn48Yg_c/s1600/Co-founders-of-google.jpg)
**Larry Page** and **Sergey Brin**(Google founders) invented **Page Rank algorithm**, used by the **Google search engine**, while they were graduate students at Stanford.

##PageRank idea and Mathematics
**Idea:** Sort pages by their relevance.

**How to count relevance(page rank)?**<br />
**Rank** of the page depends on how many pages link to it and on those pages own **Rank** and **number of outgoing links**.

**Example:**<br/>
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/webpages.jpg)

Let's represent the picture above using **directed graph:**<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/graf2.PNG)
Based on the graph we can compose a system of equations:<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/system.gif)
Where **x1, x2, x3, x4** importance of each of the pages 1-4.
