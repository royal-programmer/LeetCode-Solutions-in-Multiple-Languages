<img src="https://skillicons.dev/icons?i=python" align="right" />

# Python Default Solution - Leetcode
![Static Badge](https://img.shields.io/badge/Time_Complexity-O(N_*_M_+_(N_--_k))-blue?style=plastic)&emsp;
![Static Badge](https://img.shields.io/badge/Space_Complexity-O(N_+_k)-blue?style=plastic)&emsp;

```python3
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        result, lookup = [], set()
        for j in range(len(mat[0])):
            for i in range(len(mat)):
                if mat[i][j] or i in lookup:
                    continue
                lookup.add(i)
                result.append(i)
                if len(result) == k:
                    return result
        for i in range(len(mat)):
            if i in lookup:
                continue
            lookup.add(i)
            result.append(i)
            if len(result) == k:
                break
        return result
```
