# Trie (Prefix Tree)

```python
class TrieNode:
    def __init__(self):
        self.children = collections.defaultdict(TrieNode)
        self.is_word = False

class Trie:

    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        current = self.root
        for letter in word:
            current = current.children[letter]
        current.is_word = True

    def search(self, word):
        current = self.root
        for letter in word:
            current = current.children.get(letter)
            if current is None:
                return False
        return current.is_word

    def startsWith(self, prefix):
        current = self.root
        for letter in prefix:
            current = current.children.get(letter)
            if current is None:
                return False
        return True
```

Practice: 

- [720. Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)
- [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
- [648. Replace Words](https://leetcode.com/problems/replace-words/)
- [677. Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/)
- [1268. Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/)
- [676. Implement Magic Dictionary](https://leetcode.com/problems/implement-magic-dictionary/)
- [1023. Camelcase Matching](https://leetcode.com/problems/camelcase-matching/)

Reference:

- [Implementing a Trie in Python (in less than 100 lines of code)](https://towardsdatascience.com/implementing-a-trie-data-structure-in-python-in-less-than-100-lines-of-code-a877ea23c1a1)
