# Hash



### 49. Group Anagrams\[M\]

[https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

#### Description

Given an array of strings, group anagrams together.

**Example:**

```text
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:**

* All inputs will be in lowercase.
* The order of your output does not matter.

#### Solution

[https://leetcode.com/problems/group-anagrams/solution/](https://leetcode.com/problems/group-anagrams/solution/)

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        strs.sort()
        hash = {}
        for s in strs:
            key = self.hash_key(s)
            try:
                hash[key].append(s)
            except KeyError:
                hash[key] = [s]
        return hash.values()
    def hash_key(self, s):
        # hash string with 26 length array
        table = [0] * 26
        for ch in s:
            index = ord(ch) - ord('a')
            table[index] += 1
        return str(table)
```

### 706. Design HashMap\[E\]

[https://leetcode.com/problems/design-hashmap/](https://leetcode.com/problems/design-hashmap/)

#### Description

Design a HashMap without using any built-in hash table libraries.

To be specific, your design should include these functions:

* `put(key, value)` : Insert a \(key, value\) pair into the HashMap. If the value already exists in the HashMap, update the value.
* `get(key)`: Returns the value to which the specified key is mapped, or -1 if this map contains no mapping for the key.
* `remove(key)` : Remove the mapping for the value key if this map contains the mapping for the key.

**Example:**

```text
MyHashMap hashMap = new MyHashMap();
hashMap.put(1, 1);          
hashMap.put(2, 2);         
hashMap.get(1);            // returns 1
hashMap.get(3);            // returns -1 (not found)
hashMap.put(2, 1);          // update the existing value
hashMap.get(2);            // returns 1 
hashMap.remove(2);          // remove the mapping for 2
hashMap.get(2);            // returns -1 (not found)
```

**Note:**

* All keys and values will be in the range of `[0, 1000000]`.
* The number of operations will be in the range of `[1, 10000]`.
* Please do not use the built-in HashMap library.

#### Solution

```python

```

