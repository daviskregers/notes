# Implementation of Trie

## Creating a Trie

```
createTrie()
    create a blank root node
```

## Inserting a string in trie

There can be 4 cases:
1. The Trie is blank
2. New String's prefix is common with another strings prefix
3. New Strings prefix is already present as a complete string
4. String to be inserted is already present in the Trie

## Searching a string in Trie

There can be 3 cases:
1. String does not exist in Trie
2. String exists in Trie
3. Current string is a prefix of another String. But this string does not exist in Trie.

## Delete String from Trie

1. Some other words prefix is same as prefix of this word (BCDE, BCKG)

    Whe go back from the last node and check if no other string is dependent on it, if not, we delete the node.

2. The current word is a prefix of some other word (BCDE, BCDEF)

    In such cases we do not delete the string, just update the `end of the word` marker.

3. Some other word is a prefix of this word (BCDE, BC)
4. No one is dependent on this Word