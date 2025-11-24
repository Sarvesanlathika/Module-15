# Ex. No: 15A - Build a Binary Search Tree Using Built-in Function
# AIM
To write a Python program to build a binary search tree using a built-in function.

# ALGORITHM:
Start the program.

1.Define function _build_bst_from_sorted_values(sorted_values) → recursively build a Binary Search Tree (BST) from a sorted list.

2.Define function left_subtree(l) → print the left subtree of the BST.

3.Take user input for the number of elements.

4.Store the values in a list a.

5.Sort the list a.

6.Pass the sorted list to _build_bst_from_sorted_values() → construct the BST.

7.Print the postorder traversal of the BST.

8.Call left_subtree(l) → print the left subtree of the BST.

9.Check if the tree is a BST using the is_bst property.

10.End the program.

# PROGRAM
~~~
Reg - 212222060245 Name - Singamala Rakshitha

from binarytree import Node

# Function to build BST from sorted list using recursion
def _build_bst_from_sorted_values(sorted_values):
    if not sorted_values:
        return None
    mid = len(sorted_values) // 2
    root = Node(sorted_values[mid])
    root.left = _build_bst_from_sorted_values(sorted_values[:mid])
    root.right = _build_bst_from_sorted_values(sorted_values[mid + 1:])
    return root

# Function to print all nodes in right subtree using preorder traversal
def right_subtree(node):
    def preorder(n):
        if n:
            print(f"{n.value} -->", end="")
            preorder(n.left)
            preorder(n.right)

    print("Right Subtree :")
    preorder(node.right)
    print()

# Check if tree is BST
def is_bst(node, left=None, right=None):
    if node is None:
        return True
    if left and node.value <= left.value:
        return False
    if right and node.value >= right.value:
        return False
    return is_bst(node.left, left, node) and is_bst(node.right, node, right)

# Main block
a = []
size = int(input())
for i in range(size):
    val = int(input())
    a.append(val)

x = sorted(a)
l = _build_bst_from_sorted_values(x)

print("Postorder :", l.postorder)
right_subtree(l)
print("Is this a Binary Search Tree? ", is_bst(l))
~~~
# OUTPUT
<img width="1347" height="431" alt="image" src="https://github.com/user-attachments/assets/57c58888-d343-4a27-8707-72c2b3e5b1b1" />

# RESULT
Thus the Python program to build a binary search tree using a built-in function has been implemented and executed successfully.

# Ex. No: 15b - Build a Binary Tree with Float Values
# AIM:
To write a Python program to build a binary tree with a root, left, and right node using floating-point values.

# ALGORITHM:
1.Start the program.

2.Import the Node class from the binarytree module.

3.Create a root node using the Node class and assign a floating-point value.

4.Create left and right child nodes for the root with float values.

5.Convert the tree to a list and print the list of nodes.

End the program.

# PYTHON PROGRAM
~~~
Reg - 212222060245 Name - Singamala Rakshitha

from binarytree import Node 
l=[]
for i in range(3):
    a=input()
    l.append(a)
root=Node(l[0])
root.left=Node(l[1])
root.right=Node(l[2])
print("List of nodes :",list(root))
~~~
# OUTPUT
<img width="1189" height="334" alt="image" src="https://github.com/user-attachments/assets/7019c2ae-ac1e-4f3c-a849-f8c223c04bc8" />

# RESULT
Thus the Python program to build a binary tree with a root, left, and right node using floating-point values has been implemented and executed successfully.

# Ex. No: 15C - Expression Tree with Inorder and Postorder Traversal
# AIM
To write a Python program to build the given expression tree and print the inorder and postorder traversals.

# ALGORITHM
1.Start the program.

2.Import the required modules (build and Node from binarytree).

3.Define a list x representing the expression tree in pre-order fashion (with None for missing nodes).

4.Use the build() function to generate the binary tree.

5.Print the inorder and postorder traversal of the tree.

End the program.

# PROGRAM:
~~~
Reg - 212222060245 Name - Singamala Rakshitha

from binarytree import build
t = ["/","*","+","+",4,"-",2,3,1,None,None,9,5]
root = build(t)
print(root.inorder)
print(root.postorder)
~~~
# OUTPUT
<img width="1373" height="212" alt="image" src="https://github.com/user-attachments/assets/470c4019-c2c1-432d-8515-991b5fe6f8ed" />

# RESULT
Thus the Python program to build the given expression tree and print the inorder and postorder traversals has been implemented and executed successfully.

# Ex. No: 15D - Build a Heap Tree Using Python
# AIM
To write a Python program to build a heap tree using appropriate Python package and function.

# ALGORITHM
1.Start the program.

2.Import the heapq module.

3.Define a function heaptree(H) that takes a list H as input.

4.Use heapq.heapify(H) to convert the list into a min-heap.

5.Print the created heap.

End the program.

# PROGRAM
~~~
Reg -212222060245 Name - Singamala Rakshitha

from binarytree import heap,build,Node
def heaptree(L):
  x=L
  t=build(x)
  for i in t.values:
    print(i,"-->",end='')
  print("\nHeight : ",t.height)
  print("Is max heap? : ",t.is_max_heap)
  print("Is complete tree? : ",t.is_complete)
~~~
# OUTPUT
<img width="1251" height="254" alt="image" src="https://github.com/user-attachments/assets/76584a64-b97e-47ba-887d-ad17c2bac395" />

# RESULT
Thus the Python program to build a heap tree using appropriate Python package and function has been implemented and executed successfully.

# Ex. No: 15E - Build and Evaluate an Expression Tree
# AIM
To write a Python program to build and evaluate the given Expression tree.

# ALGORITHM
1.Start the program.

2.Create nodes for operators and operands. Build the expression tree by connecting nodes in the correct hierarchical structure.

3.Define a recursive function evaluate(root): If the node is a number (leaf), return it.

4.Else, recursively evaluate left and right subtrees. Apply the operator at the current node to the results. Return the final result from the root node.

5.End the program.

# PROGRAM
~~~
Reg - 212222060245 Name - Singamala Rakshitha
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
 

def isLeaf(node):
    return node.left is None and node.right is None
 
def process(op, x, y):
    if op == '+':
        return x + y
    if op == '-':
        return x - y
    if op == '*':
        return x * y
    if op == '/':
        return x / y
 
def evaluate(root):
~~~
# OUTPUT
<img width="1259" height="180" alt="image" src="https://github.com/user-attachments/assets/ef95c78d-fd21-40f8-a306-ab6a4381f687" />


# RESULT
Thus the Python program to build and evaluate the given Expression tree has been implemented and executed successfully.
