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
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/graf2.PNG)<br />
Based on the graph we can compose a system of equations:<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/system.gif)<br />
Where **x1, x2, x3, x4** importance(rank) of each of the pages 1-4.<br />

Let's find **PageRank** vector using method for **dynamical systems**:<br />
To find it we have to find the last value of the vector in the sequence "**v, Av, A^2v..., A^kv**" before it becomes the equilibrium value.<br />
v - initial rank vector (Suppose that initially the importance is uniformly distributed among the 4 nodes, each getting ¼)<br />
A - transition matrix of the system above =>

A = ![alt text](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/matrix.gif)<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/rezultate_1.gif)<br />

Based on gotten **PageRank vector** the search result would be:<br />
1. Page1
2. Page3
3. Page4
4. Page2

##Difficulties that might arise and their Solution
###Nodes with no outgoing edges (dangling nodes)
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/graf3.PNG)<br />
We iteratively compute the rank of the 3 pages:<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/vectors2.gif)<br />
So in this case the rank of every page is 0. This is counterintuitive, as page 3 has 2 incoming links, so it must have some importance!

###Disconnected components
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/componente.PNG)<br />
A random surfer that starts in the first connected component has no way of getting to web page 5 since the nodes 1 and 2 have no links to node 5 that he can follow.<br />
The transition matrix for this graph is:<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/RV.GIF)<br />
![alt tag](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/uv2.GIF) are both eigenvectors<br />
corresponding to the eigenvalue 1, and they are not just trivially one the a scalar multiple of the other. So, both in theory and in practice, the notation of ranking pages from the first connected component relative to the ones from the second connected component is ambiguous.

###The solution of Page and Brin:
In order to overcome these problems, fix a positive constant p between 0 and 1, which we call the damping factor (a typical value for p is 0.15). Define the Page Rank matrix (also known as the Google matrix) of the graph by ![alt text](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/M.GIF) where ![alt text](http://www.math.cornell.edu/~mec/Winter2009/RalucaRemus/Lecture3/Images/B1.GIF)<br />
 M models the random surfer model as follows: most of the time, a surfer will follow links from a page: from a page i the surfer will follow the outgoing links and move on to one of the neighbors of i. A smaller, but positive percentage of the time, the surfer will dump the current page and choose arbitrarily a different page from the web and "teleport" there. The damping factor p reflects the probability that the surfer quits the current page and "teleports" to a new one. Since he/she can teleport to any web page, each page has   probability to be chosen. This justifies the structure of the matrix B.
