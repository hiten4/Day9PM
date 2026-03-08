Q1 Conceptual

Consider:

t = ([1,2], [3,4])

Can we run:

t[0][0] = 99

Answer

Yes, this statement works and does not raise an error.

Even though tuples are immutable, the immutability only applies to the tuple structure itself, not to the objects stored inside it.

The tuple t contains two lists, and lists are mutable objects. When we run:

t[0][0] = 99

we are modifying the content of the list, not replacing the tuple element.

What is not allowed is reassigning the tuple element itself:

t[0] = [99,2]   # This will raise TypeError

Key takeaway

Tuple = immutable container

Objects inside the tuple can still be mutable

Mutating the object is allowed, replacing the object is not

Q2 Coding — Duplicate Detection

Function that returns elements appearing more than once using only set logic.

def find_duplicates(lst):
    seen = set()
    duplicates = set()

    for item in lst:
        if item in seen:
            duplicates.add(item)
        else:
            seen.add(item)

    return duplicates

Example:

find_duplicates([1,2,3,2,4,5,3])

Output:

{2,3}

Time Complexity

O(n) because we traverse the list once and set lookup is O(1).

Q3 Debug Problem

Buggy code:

def unique_to_each(a, b):
    result = set(a) - set(b)
    return list(result)
Why the issue occurs

The expression:

set(a) - set(b)

returns elements that exist in a but not in b.

For:

a = [1,2,3]
b = [3,4,5]

This gives:

{1,2}

However, the expected result requires elements unique to both lists, meaning:

elements in a but not in b

elements in b but not in a

Fixed Function
def unique_to_each(a, b):
    set_a = set(a)
    set_b = set(b)

    unique = (set_a - set_b) | (set_b - set_a)

    return list(unique)

Test:

unique_to_each([1,2,3], [3,4,5])

Output:

[1,2,4,5]

This solution uses set difference and union operations and runs in O(n) time.
