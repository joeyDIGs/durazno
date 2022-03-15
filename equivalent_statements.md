
# A&M Problem Solving Interview Question - Statement Equivalence

## Intro
A statement can be represented as a list or array of words. As an example, the statement "I love Luci" could be defined as `statement = ["I", "love", "Luci"]`.

Further, we can represent word equirvalence in an array of tuples. For example `equivalentPairs = [('love', 'like'), ('dinner', 'meal')]` shows that the words `love` and `like` are
equivalent, and so are `meal` and `dinner`.


## Task
Given an array of `equivalentPairs` and two statements `stt1` and `stt2`, return True if the two statements are equivalent, otherwise return False.

Notes:
- Two statements can only be equivalent if they are the same length
- Two statements can only be equivalent if for each word `i` `stt1[i]` is equivalent to `stt2[i]`
- Equivalence is a reflexive relation, meaning that a word is equivalent to itself
- Equivalence is a symetric relation, meaning that if A and B are equivalent then B and A are also equivalent
- Equivalence is a transitive relation, meaning that if A and B are equivalent and B and C are equivalent, then A and C must also be equivalent


 

Example 1:

```python
# Input: 
statement1 = ["wonderful","acting","skills"]
statement2 = ["quality","drama","talent"]
equivalentPairs = [("wonderful","good"),("quality","good"),("drama","acting"),("skills","talent")]

# Output:
True

# Explanation: The two sentences have the same length and each word i of statement1 is also equivalent to the corresponding word in statement2.  
```

Example 2:

```python
# Input: 
statement1 = ["I","love","hackerrank"]
statement2 = ["I","love","naruto"]
equivalentPairs = [("manga","naruto"),("canvas","anime"),("hackerrank","canvas"),("anime","manga")]

# Output: 
True

# Explanation: "hackerrank" --> "canvas" --> "anime" --> "manga" --> "naruto".
# Since "hackerrank is equivalent to "naruto" and the first two words are the same, the two sentences are equivalent.
```

Example 3:

```python
# Input: 
statement1 = ["I","love","hackerrank"]
statement2 = ["I","love","naruto"]
equivalentPairs = [("manga","hunterXhunter"),("canvas","anime"),("hackerrank","canvas"),("anime","manga")]

# Output: 
False

# Explanation: "hackerrank" is not equivalent to "naruto".
``` 

Constraints:

- 1 <= statement1.length, statement2.length <= 1000
- 1 <= statement1[i].length, statement2[i].length <= 20
- statement1[i] and statement2[i] consist of lower-case and upper-case English letters.
- 0 <= equivalentPairs.length <= 2000
- equivalentPairs[i].length == 2
- 1 <= x[i].length, y[i].length <= 20
- x[i] and y[i] consist of English letters.


