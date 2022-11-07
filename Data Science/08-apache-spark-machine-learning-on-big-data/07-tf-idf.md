# TF / IDF

The python file available here:

https://github.com/daviskregers/data-science-recap/blob/main/28-spark-wikipedia-search-tf-idf.py

---

## TF-IDF

- Stands for Term Frequency and Inverse Document Frequency
- Important data for search - figures out what terms are most relevant for a document

- Term Frequency just measures how often a word occurs in a document
    - A word that occurs frequently is probably important to that document's meaning
- Document Frequency is how often, a word occurs in an entire set of documents, i.e., all of Wikipedia or every web page
    - This tells us about common words that just appear everywhere no matter what the topic, like "a", "the", "and" etc.

- So a measure of the relevancy of a word to a document might be $$\frac{term frequency}{document frequency}$$
- Or $$ Term frequency * Inverse Document Frequency $$
- That is, take how often the word appears in a document, over how often it just appears everywhere. That gives you a measure of how important and unique this word is for this document.

## TF-IDF in practice

- We actually use the log of the IDF, since word frequencies are distributed exponentially. That gives us a better weighting of a words overall popularity.
- TF-IDF assumes document is just a "bag of words"
    - Parsing documents into a bag of words can be most of the work
    - Words can be represented as a has value (number) for efficiency
    - What about synonyms? Various tenses? Abbreviations? Capitalizations? Misspelling?
- Doing this at scale is the hard part
    - That's where Spark comes in!

## Using TF-IDF

- A very simple search algorithm could be:
    - Compute TF-IDF for every word in a corpus
    - For a given search word, sort the documents by their TF-DF score for that word
    - Display the results
