## Degree_of_Profanity

### Assumptions:

* The provided set of racial slurs is a list of words in lowercase.
* A sentence is a sequence of characters separated by punctuation, such as periods, exclamation points, and question marks.
* The degree of profanity for a sentence is the percentage of words in the sentence that are racial slurs.

### Code

```import string

# set of racial slurs
racial_slurs = {'word1', 'word2', 'word3'}

# function to calculate the degree of profanity for a sentence
def calculate_degree_of_profanity(sentence):
    words = sentence.lower().translate(str.maketrans('', '', string.punctuation)).split()
    num_slurs = len([word for word in words if word in racial_slurs])
    return (num_slurs / len(words)) * 100 if len(words) > 0 else 0

# read the tweets file and process each sentence
with open('/content/drive/MyDrive/assignment/tweets.txt', 'r') as f:
    for line in f:
        sentences = line.split('.')
        for sentence in sentences:
            degree_of_profanity = calculate_degree_of_profanity(sentence)
            print(f'Sentence: {sentence.strip()}')
            print(f'Degree of Profanity: {degree_of_profanity}%')
            print()
```

