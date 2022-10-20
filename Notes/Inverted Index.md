
An inverted index is an index [[data structure]] storing a mapping from content, such as words or numbers, to its locations in a document or a set of documents. In simple words, it is a hashmap like data structure that directs you from a word to a document or a web page.

There are two types of inverted indexes: A **record-level inverted index** contains a list of references to documents for each word. A **word-level inverted index** additionally contains the positions of each word within a document. The letter form offers more functionality, but needs more processing power and space to be created. 

Suppose we want to search the texts “hello everyone, ” “this article is based on inverted index, ” “which is hashmap like data structure”. If we index by (text, word within the text), the index with location in text is:

 ```
hello                (1, 1)
 everyone             (1, 2)
 this                 (2, 1)
 article              (2, 2)
 is                   (2, 3); (3, 2)
 based                (2, 4)
 on                   (2, 5)
 inverted             (2, 6)
 index                (2, 7)
 which                (3, 1)
 hashmap              (3, 3)
 like                 (3, 4)
 data                 (3, 5)
 structure            (3, 6)

```

 **Steps to build an inverted index:**

-   **Fetch the Document**   
    Removing of Stop Words: Stop words are most occurring and useless words in document like “I”, “the”, “we”, “is”, “an”.
-   **Stemming of Root Word**   
    Whenever I want to search for “cat”, I want to see a document that has information about it. But the word present in the document is called “cats” or “catty” instead of “cat”. To relate the both words, I’ll chop some part of each and every word I read so that I could get the “root word”. There are standard tools for performing this like “Porter’s Stemmer”.
-   **Record Document IDs**   
    If word is already present add reference of document to index else create new entry. Add additional information like frequency of word, location of word etc.

**Example:**

```
Words                 Document
ant                   doc1
demo                  doc2
world                 doc1, doc2
```
**Advantage of Inverted Index are:** 

-   Inverted index is to allow fast full text searches, at a cost of increased processing when a document is added to the database.
-   It is easy to develop.
-   It is the most popular data structure used in document retrieval systems, used on a large scale for example in search engines.
