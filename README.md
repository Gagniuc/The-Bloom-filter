# The Bloom filter

Ex. (19) – <strong>Aho–Corasick</strong> multi-pattern scan appears here in Python. Although the syntax is Python-specific, the core idea mirrors the usual form of the algorithm. This code sample is one entry in a suite of 127 algorithms set out in <i>[Antivirus Engines: From Methods to Innovations, Design, and Applications](https://github.com/Gagniuc/Antivirus-Engines)</i> (Elsevier Syngress, 2024).

***

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

# create a Bloom filter of 
# size 100 with two hash functions.

b = B(100, [hash, hash])

# add items
b.a("s1")
b.a("s2")

# check membership
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

