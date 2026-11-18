# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input string from the user.


### Step2:
Calculate the frequency of occurrence of each character.

### Step3:
Create tree nodes for each character and its frequency.


### Step4:
Build the Huffman tree by combining the two nodes with the lowest frequencies until one node remains.


### Step5:
Generate and print the Huffman codes for each character.

 
## Program:

```
import heapq
from collections import Counter

# Create tree nodes
class Node:
    def __init__(self, char, freq):
        self.char = char
        self.freq = freq
        self.left = None
        self.right = None

    def __lt__(self, other):
        return self.freq < other.freq

# Main function to implement Huffman coding
def huffman_coding(text):
    frequency = Counter(text)

    heap = [Node(char, freq) for char, freq in frequency.items()]
    heapq.heapify(heap)

    while len(heap) > 1:
        left = heapq.heappop(heap)
        right = heapq.heappop(heap)

        new_node = Node(None, left.freq + right.freq)
        new_node.left = left
        new_node.right = right

        heapq.heappush(heap, new_node)

    codes = {}

    def generate_codes(node, code):
        if node is None:
            return

        if node.char is not None:
            codes[node.char] = code if code else "0"
            return

        generate_codes(node.left, code + "0")
        generate_codes(node.right, code + "1")

    generate_codes(heap[0], "")

    print("Character and Huffman Code:")
    for char, code in codes.items():
        print(char, ":", code)

# Get the input string
text = input("Enter the string: ")

huffman_coding(text)
```

## Output:

<img width="272" height="170" alt="image" src="https://github.com/user-attachments/assets/2f3d1128-beae-4152-8c34-74aeb17360af" />




## Result
Thus the huffman coding was implemented to compress the data using python programming.
