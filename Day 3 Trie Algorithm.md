

## 🔸 Trie Algorithm

A **Trie** is a tree-like data structure used for storing strings. It is very efficient for solving problems related to:

* **Prefix searching**
* **Autocomplete**
* **Dictionary word lookups**

---

## ✅ Java Implementation of Trie

### 1. TrieNode Class

```java
class TrieNode {
    TrieNode[] children = new TrieNode[26]; // For 'a' to 'z'
    boolean isEndOfWord = false;

    TrieNode() {
        for (int i = 0; i < 26; i++)
            children[i] = null;
    }
}
```

---

### 2. Trie Class with Insert, Search, StartsWith

```java
class Trie {
    private TrieNode root;

    public Trie() {
        root = new TrieNode();
    }

    // Insert a word into the trie
    public void insert(String word) {
        TrieNode current = root;

        for (char ch : word.toCharArray()) {
            int index = ch - 'a';

            if (current.children[index] == null)
                current.children[index] = new TrieNode();

            current = current.children[index];
        }

        current.isEndOfWord = true;
    }

    // Search a full word
    public boolean search(String word) {
        TrieNode current = root;

        for (char ch : word.toCharArray()) {
            int index = ch - 'a';

            if (current.children[index] == null)
                return false;

            current = current.children[index];
        }

        return current.isEndOfWord;
    }

    // Check if a prefix exists
    public boolean startsWith(String prefix) {
        TrieNode current = root;

        for (char ch : prefix.toCharArray()) {
            int index = ch - 'a';

            if (current.children[index] == null)
                return false;

            current = current.children[index];
        }

        return true;
    }
}
```

---

### 3. Main Method to Use the Trie

```java
public class TrieExample {
    public static void main(String[] args) {
        Trie trie = new Trie();

        trie.insert("apple");
        trie.insert("app");
        trie.insert("bat");

        System.out.println(trie.search("apple"));   // true
        System.out.println(trie.search("app"));     // true
        System.out.println(trie.search("ap"));      // false
        System.out.println(trie.startsWith("ap"));  // true
        System.out.println(trie.search("bat"));     // true
        System.out.println(trie.startsWith("cat")); // false
    }
}
```

---

* Trie is efficient for word search, prefix search, and autocomplete.
* It uses a tree with nodes for each character.
* Commonly used in search engines, spell-checkers, and dictionaries.

---

