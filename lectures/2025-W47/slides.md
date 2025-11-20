  # Python Basics & Data Structures Part 4

  - Open Codespaces
  - https://github.com/codespaces/

notes:
- last week we talked about Tuples & Dicts
- This week we're going to talk about Sets

    ---slide---

  ## Sets: Unique Collections

  - Sets are unordered collections of **unique** items
  - No duplicates allowed
  - Great for membership testing and removing duplicates.

notes:
- sets are like lists
- but for uniqueness
- it's simple, no duplicates
- you can perform set theory operations (math) 
- let's dive straight in...

    ---slide---

  ### Creating Sets

  ```python
  # With data
  unique_ages = {25, 34, 45, 52, 61}
  diagnoses = {"Diabetes", "Hypertension", "Asthma"}

  # From a list (automatically removes duplicates)
  numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
  unique_numbers = set(numbers)  # {1, 2, 3, 4}

  # Empty set (must use set(), not {})
  empty = set()
  ```

notes:
- we use curly brackets like dictionaries
- but they're not pairs, just singletons
- like a list but `{}` instead of `[]`

    ---slide---
  ### Set Operations

  ```python
  fruits = {"apple", "banana", "cherry"}

  # Add item
  fruits.add("date")

  # Add multiple items
  fruits.update(["elderberry", "fig"])

  # Remove and return arbitrary item
  item = fruits.pop()
  ```
notes:
- let's try these examples
    ---slide---

  ```python
  # Remove item (error if not found)
  fruits.remove("banana")

  # Remove item (no error if not found)
  fruits.discard("banana")

  # Clear all items
  fruits.clear()

  # Length
  len(fruits)
  ```
notes:
- error vs. no error
- `len` operator works like lists, tuples and dicts
- unlike list, there is no "count" method
- dict keys behave like sets
    ---slide---

  ```python
  # Check membership (VERY FAST)
  "apple" in fruits      # True
  "zebra" in fruits      # False
  ```

notes:
- if speed matters, turning a list into a set is useful for multiple queries
- it's not that sets count faster
- the hard work is done by turning it into a set
    ---slide---
  ### Set Mathematics

  ```python
  # Two sets of patients
  diabetic = {"P001", "P004", "P007", "P015"}
  hypertensive = {"P002", "P004", "P008", "P015", "P017"}

  # Union (all patients with either condition)
  either = diabetic | hypertensive
  # or: diabetic.union(hypertensive)
  # {"P001", "P002", "P004", "P007", "P008", "P015", "P017"}

  # Intersection (patients with BOTH conditions)
  both = diabetic & hypertensive
  # or: diabetic.intersection(hypertensive)
  # {"P004", "P015"}
  ```
notes:
- let's take a look at set mathematics
- "&" and "|" are the "and" & "or" operators
- "&": ampersand, the "and" sign
- "|": pipe, bar, the "or" sign
- idiomatic for the methods "intersection" and "union"
- in logic:
  - "and" is like intersection
  - "or" is like union

    ---slide---
  ```python
  # Difference (diabetic but not hypertensive)
  only_diabetic = diabetic - hypertensive
  # or: diabetic.difference(hypertensive)
  # {"P001", "P007"}

  # Symmetric difference (one condition but not both)
  only_one = diabetic ^ hypertensive
  # or: diabetic.symmetric_difference(hypertensive)
  # {"P001", "P002", "P007", "P008", "P017"}

  # Subset and Superset checks
  small_set = {"P001", "P004"}
  small_set.issubset(diabetic)    # True
  diabetic.issuperset(small_set)  # True
  ```
notes:
- a few more examples
- I should mention that I get these wrong all the time!
- and these are not commutative, order matters

    ---slide---
  ### Common Use Cases

  **1. Remove duplicates:**
  ```python
  observations = [15, 8, 22, 15, 19, 8, 31, 12, 22, 27, 18]
  unique_counts = set(observations)
  print(f"Unique observation counts: {sorted(unique_counts)}")
  ```

  **2. Fast membership testing:**
  ```python
  # List: slow for large collections
  valid_ids = ["P001", "P002", ..., "P9999"]  # 10,000 items
  "P5000" in valid_ids  # Checks every item (slow)

  # Set: very fast
  valid_ids = {"P001", "P002", ..., "P9999"}  # 10,000 items
  "P5000" in valid_ids  # Instant lookup (fast)
  ```
notes:
- the obvious case for unique counts
- btw: a lot of businesses (FB, Netflix, Spotify)
  - report unique visitors (in quarterly reports)
  - this is how they do it
  - cookies, IP, MAC address (media access control)
  - a unique identifier for a network-connected device, like a computer or smartphone

    ---slide---

  **3. Find common/unique elements:**
  ```python
  site_a_species = {"Bald Eagle", "Red Fox", "Deer"}
  site_b_species = {"Red Fox", "Wolf", "Bear", "Deer"}

  # Species at both sites
  common = site_a_species & site_b_species
  # {"Red Fox", "Deer"}

  # Species only at site A
  unique_a = site_a_species - site_b_species
  # {"Bald Eagle"}
  ```

notes:
- for comparisons

    ---slide---
  # In Summary
  ## Core Data Types


  - int: `3`
  - float: `3.14159`
  - str: `"pi"`
  - boolean: `True == 1`

    ---slide---

  ## Core Data Structures

  - list: `[1, 2, 3]`
  - tuple: `(4, 5, 6)`
  - dict: `{"pi": 3.14159, "euler": 2.71828}`
  - set: `{1, 2, 1, 3, 2}`

notes:
- when we return, we will dive into flow control