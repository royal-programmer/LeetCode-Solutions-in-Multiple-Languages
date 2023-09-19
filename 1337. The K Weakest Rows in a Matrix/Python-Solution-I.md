<img src="https://skillicons.dev/icons?i=python" align="right" />

# Python Default Solution - Leetcode

```python3
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        count = [i.count(1) for i in mat]
        temp = count.copy()
        temp.sort()
        res = []
        for i in range(k):
            res.append(count.index(temp[i]))
            count[res[i]] = 'X'
        return res
```
