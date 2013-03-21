

Problem Definition
------------------------------------------------------
A tree like data structure, lets call it 4Tree is a tree in which each node has either 0 or 4 children.We are given two 4Trees, each representing a colour. In the tree,a node can either be black or white or mixed coloured.In case ,it is black or white,it is a leaf node.In case it is a mixed node,it will have 4 children,each of which can be black,white or mixed.Given two 4Trees,we have to construct a tree which is an overlay of the 2 trees. Overlay of 2 black nodes is black and even if one of the nodes is white,the overlay is white. Overlay of a non-leaf node and leaf node is overlay of all the children of non-leaf node with the leaf node.


Solution in C!
-------------------------------------------------------

To run the code(Usage):
````````````````
$ ./4tree 4tree1 4tree2

// Where 4tree2 and 4tree2 are the Depth First Traversal of the trees



Example run1:
````````````
Valay-Shahs-MacBook-Pro:Neon valayshah$ ./4tree MMBBBBMBBBBMBBBBMBBBB MWMBBWBBMMBBBBMBBBBMBBBBMBBBB

Displaying 4Tree 1! 
MMBBBBMBBBBMBBBBMBBBB

Displaying  4Tree 2! 
MWMBBWBBMMBBBBMBBBBMBBBBMBBBB

Displaying  Merged 4Tree! 
MWMBBWBBMBBBB



Example run2: 
`````````````
Valay-Shahs-MacBook-Pro:Neon valayshah$ ./4tree MMBBBBMBBBBMBBBBMBBBB MWMBBWBBB

Displaying 4Tree 1! 
MMBBBBMBBBBMBBBBMBBBB

Displaying  4Tree 2! 
MWMBBWBBB

Displaying  Merged 4Tree! 
MWMBBWBBB


// I also took care of some of the corner cases!


Thank you for reading!


