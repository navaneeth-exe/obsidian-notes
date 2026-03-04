Module: [[ADS Module 3]]

## 1. Definition

A **Trie** is a tree-based data structure used to store a collection of strings in a hierarchical manner.  
It is mainly used for **efficient prefix searching**.

Each node represents a character of a string.  
The path from root to a node represents a prefix of stored words.

---

## 2. Structure of Trie

A Trie node contains:

- Array of child pointers (usually size 26 for lowercase letters)
- Boolean variable `isEndOfWord`

### Structure Representation in C:

```c
#define ALPHABET_SIZE 26

struct TrieNode {
    struct TrieNode *children[ALPHABET_SIZE];
    int isEndOfWord;
};
```

---

## 3. Basic Operations

### (1) Insertion

**Algorithm:**

1. Start from root.
2. For each character in word:
    - Find index = character - 'a'
    - If child does not exist, create new node.
    - Move to child node.
3. After last character, mark `isEndOfWord = 1`.

**Time Complexity:** O(L)  
Where L = length of word.

---

### (2) Searching

**Algorithm:**

1. Start from root.
2. For each character:
    - Move to corresponding child.
    - If child is NULL → word not present.
3. After last character:
    - If `isEndOfWord = 1` → word found.

**Time Complexity:** O(L)

---

### (3) Deletion

Deletion removes a word from the Trie and may remove unnecessary nodes.

**Time Complexity:** O(L)

---

## 4. Example

If we insert:

```
cat
car
bat
```

Trie Structure:

```
        (root)
        /    \
       c      b
       |      |
       a      a
      / \      |
     t   r      t
```

Here:

- "cat" and "car" share prefix "ca"
- "bat" is separate branch

---

## 5. Advantages

- Fast prefix searching
- No hash collision
- Efficient for dictionary implementation
- Used in auto-complete systems

---

## 6. Disadvantages

- High memory usage
- Wastes space if few words stored
- Not suitable for very large character sets

---

## 7. Applications

- Auto-complete systems
- Spell checking
- Dictionary implementation
- IP routing
- Word games

---

## 8. Conclusion

A Trie is an efficient data structure for storing and searching strings based on prefixes.  
It provides O(L) time complexity for insertion and search operations, making it useful in applications involving large dictionaries and prefix queries.