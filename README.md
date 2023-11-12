# TextAnalysisWordCount
This script reads a text file, converts the text to lowercase, removes punctuation, and then counts the occurrences of each word. You can use this script to perform basic text analysis on a given document.

# word_counter.py

from collections import Counter
import string

def count_words(filename):
    """
    Count the occurrences of each word in a text file.

    Args:
    - filename (str): The name of the text file.

    Returns:
    - Counter: A Counter object with word frequencies.
    """
    with open(filename, "r") as file:
        # Read the content and convert to lowercase
        content = file.read().lower()
        
        # Remove punctuation
        content = content.translate(str.maketrans("", "", string.punctuation))

        # Split the text into words
        words = content.split()

        # Count the occurrences of each word
        word_counts = Counter(words)

    return word_counts

if __name__ == "__main__":
    # Input: Provide the name of the text file
    filename = input("Enter the name of the text file: ")

    try:
        # Count words in the provided file
        word_counts = count_words(filename)

        # Display the results
        print("\nWord frequencies:")
        for word, count in word_counts.items():
            print(f"{word}: {count}")

    except FileNotFoundError:
        print(f"Error: The file '{filename}' was not found.")
