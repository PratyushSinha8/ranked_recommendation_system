# ranked_recommendation_system

#Building User Tag Matrix (UTM) and User Tag Vectors (UTV)
A Flattened UTM is a UTV 

Each row (question) in a UTM is represented by a **Tag Set**

As a Tag Set represents a question's options (tags), the set of values represent the **Relative Interest (RI)** in those options (tags) by percentage

For eg:

If for question 1 for User 1, the rankings out of 5 options (tags) are in the order : 2, 3, 4, 1, 5
Therefore, the **Relative Interest (RI)** in those options (tags) are:
26.6%, 20%, 13.3%, 33.3%, 6.7%

The **RI** is is smilarly calculated for all the **Tag Sets** and we obtain a **User Tag Vector**

So for a given query set of tags T, a user's interest in those tags can be found as a mean of the RI in all the respective tags in T.

*The reason why we're taking a mean is because for a given query T, the interest in those tags of a user is determined by the RI in those tags. Even if more than 1 tag is in the query T, the RI in those tags still hold true, and hence we take a mean value of all the individual RI. This can help us answer questions involving Top N users for a given destination (query tag T), or users associated to a given set of tags in general*

Eg:

The given set of options (tags) are arranged as follows in the questionnaire,
Let's called it the **Questionnaire Matrix (QM)**:

[

  [Adventure, Relax, Educational, Spiritual Retreat, Religious Tourism],

  [Mountains, Beaches, Forests, City Landscapes],

  [Summer, Winter, Autumn, Spring]

]


Let's take a query set of tags **T** describing  **destination (or anything, really)**:

  {Mountains, Adventure, Summer, Relax}


The rankings of User U1 are as follows:
[
  
  [1, 4, 5, 2, 3]

  [4, 3, 1, 2]

  [1, 2, 4, 3]

]

The rankings of User U2 are as follows:
[
  
  [4, 2, 3, 5, 1],

  [1, 3, 2, 4],

  [3, 2, 4, 1]

]

- Each row is a **Tag Set**
- For finding RI for U1 in Tag Set 1:

We have 5 options. Hence x +2x +3x +4x + 5x = 100 (Quantifying value through an Arithmetic Progression)

Therefore, calculating it and assigning respective weightage according to the user's ranking, we get the following RI:

[33.3%, 13.3%, 6.7%, 26.6%,  20%]

This way, calculating the whole UTM for U1, we get:

[

  [**33.3%**, **13.3%**, 6.7%, 26.6%,  20%],

  [**10%**, 20%, 40%, 30%],

  [**40%**, 30%, 10%, 20%]

]

Similarly UTM for U2:

[

  [**13.3%**, **26.6%**, 20%, 6.7%, 33.3%],

  [**40%**, 20%, 30%, 10%],

  [**20%**, 30%, 10%, 40%]

]

- Now picking out the respective RIs of tags in query tag T, for each user and forming **User Interest Vectors (UIV)** for the given destination T:

U1: [10%, 33.3%, 40%, 13.3%]

U2: [40%, 13.3%, 20% 26.6%]

For U1:, Mean User Interest (MUI) in the given destination T
=

(10+33.3+40+13.3)/4= 24.15

For U2:, Mean User Interest (MUI) in the given destination T
=

(40+13.3+20+26.6)/4= 24.975




Hence here, U2 would be a more preferred User for Destination T.

** To involve non-selection of options while ranking, we could associate them with the single-option questions (tag == 0 or 1).





