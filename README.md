# The Bloom filter

Ex. (20) - <strong>Bloom filter</strong> membership test structure appears here in Python. Though the syntax is Python-specific, the core idea stays identical. This snippet belongs to the set of 127 algorithms in <i>[Antivirus Engines: From Methods to Innovations, Design, and Applications](https://github.com/Gagniuc/Antivirus-Engines)</i> (Elsevier Syngress, 2024).

***

The code from above defines a Python class named <code>B</code> that implements a basic Bloom-filter data structure. A Bloom filter is a probabilistic data structure used for membership testing, particularly for efficiently checking whether an element is a member of a set or not. The <code>B</code> class is initialized with two parameters: <code>n</code> and <code>h</code>. <code>n</code> determines the size (number of bits) of the Bloom filter bit array, representing its capacity to store elements. <code>h</code> is a list of hash functions used by the filter for hashing items. Multiple hash functions are employed to distribute elements across the bit array. The constructor method (<code>init</code>) initializes the Bloom filter by setting its size, creating a bit array (initialized with zeros), and storing the provided hash functions. The <code>a</code> method allows one to add items to the Bloom filter. For each hash function in the <code>h</code> list, it computes an index in the bit array by applying the hash function to the item and taking the modulo of the result with the size of the filter. It then sets the corresponding bit in the bit array to 1, indicating that this item is present (or might be present) in the filter. The <code>contains</code> method overloads the <code>in</code> operator, allowing one to check if an item is present in the filter. For each hash function in the <code>h</code> list, it computes an index in the bit array in the same way as the <code>a</code> method. If any of the corresponding bits in the bit array are 0, it immediately returns <code>False</code>, indicating that the item is definitely not present in the filter. If all corresponding bits are 1, it returns <code>True</code>, indicating that the item might be present in the filter. However, false positives are possible. The example usage demonstrates how to create a <code>B</code> instance with a size of 100 and two hash functions (the built-in <code>hash</code> function).

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

