# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1: Get the input string from the user
<br>

### Step2:
<br> Calculate the frequency of each character in the string

### Step3:
<br>Sort the characters in increasing order of the frequency. 

### Step4:
<br> Remove the minimum frequencies and add the sum into the list of frequencies
### Step5:
<br> Repeat the steps 2 and 3 until a single tree is created.
## Step5: 
<br> End the execution 

 
## Program:

``` Python
# Get the input String
string = '212221230125 Vismaya.S'


# Create tree nodes
class NodeTree(object):
    def __init__(self, left=None, right=None):
        self.left = left
        self.right = right
    def children(self):
        return (self.left, self.right)

# Main function to implement huffman coding
def huffman_code_tree(node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l,r) = node.children()
    d = dict()
    d.update(huffman_code_tree(l, True, binString + '0'))
    d.update(huffman_code_tree(r, False, binString + '1'))
    return d


# Calculate frequency of occurrence
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
        
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes = freq
            
while len(nodes) > 1:
    (key1, c1) = nodes[-1]
    (key2, c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1, key2)
    nodes.append((node, c1 + c2))
    nodes = sorted(nodes, key = lambda x: x[1], reverse=True)

# Print the characters and its huffmancode

huffmanCode = huffman_code_tree(nodes[0][0])
print(' Char | Huffman code')
print('-----------')
for (char, frequency) in freq:
    print('%-4r | %12s' % (char, huffmanCode[char]))



```
## Output:

### Print the characters and its huffmancode
<br>![huff](https://github.com/VismayaNair/Huffman-Coding/assets/93427210/8cb63463-2ccf-4284-88cd-e95231d5f35f)

<br>
<br>
<br>
<br>
<br>



## Result
Thus the huffman coding was implemented to compress the data using python programming.
