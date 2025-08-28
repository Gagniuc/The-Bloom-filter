# The Bloom filter

Ex. (20) – <strong>Bloom filter</strong> membership test structure appears here in Python. Though the syntax is Python-specific, the core idea stays identical. This snippet belongs to the set of 127 algorithms in <i>Antivirus Engines: From Methods to Innovations, Design, and Applications</i> (Elsevier Syngress, 2024).

***

The Bloom filter
The code above implements a basic Bloom filter using a Python class with all variable and method names reduced to single letters. The class B represents the Bloom filter data structure. It is initialized with two parameters: n for the size (number of bits) of the bit array storing membership information, and h for the list of hash functions used to disperse items across the bit array. The constructor sets up the filter’s size, creates the bit array (b), and stores the hash functions (h). The method a is used to add elements to the filter; for each hash function in the list, it computes an index by applying the hash function to the item and taking the result modulo n, then sets the corresponding position in the array b to 1, marking the potential presence of the item. The contains method supports membership checks with the in operator; it computes indices in the same way as adding, but if it finds any position in b unset (equal to 0), it returns False, proving the item is not present. If all relevant positions are set, it returns True, signaling the item might be present—but with a chance of false positives. The usage example shows the creation of a Bloom filter using B with a size of 100 and two hash functions, adding “s1” and “s2” to the filter, and checking membership for “s1” (which is present) and “s3” (which is definitely absent).

## Native implementation in Python

```python
class B:
    def __init__(s, n, h):
        s.s = n
        s.b = [0] * n
        s.h = h

    def a(s, x):
        for f in s.h:
            i = f(x) % s.s
            s.b[i] = 1

    def __contains__(s, x):
        for f in s.h:
            i = f(x) % s.s
            if s.b[i] == 0:
                return False
        return True

b = B(100, [hash, hash])

b.a("s1")
b.a("s2")

print("Is 's1' in the filter?", "s1" in b)
print("Is 's3' in the filter?", "s3" in b)
``` 

```text
Output:
Is 's1' in the filter? True
Is 's3' in the filter? False
```

## References

- <i>Paul A. Gagniuc. Antivirus Engines: From Methods to Innovations, Design, and Applications. Cambridge, MA: Elsevier Syngress, 2024. pp. 1-656.</i>

***

