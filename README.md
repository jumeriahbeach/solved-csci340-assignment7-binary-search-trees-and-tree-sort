Download Link: https://assignmentchef.com/product/solved-csci340-assignment7-binary-search-trees-and-tree-sort
<br>
<sup>                             </sup><strong> </strong>

For this computer assignment, implement a derived class (as a template) to represent a binary search tree. Since a binary search tree is also a binary tree, implement your binary search tree class from the base class of binary trees, which you implemented in your previous assignment.

The definition of the derived class of a binary search tree (as a template) is given as follows:

<table width="0">

 <tbody>

  <tr>

   <td width="336">template &lt; class T &gt;class binSTree : public binTree &lt; T &gt; { public:</td>

   <td width="189"> </td>

  </tr>

  <tr>

   <td width="336">            void insert ( const T&amp; x );</td>

   <td width="189">// inserts node with value x</td>

  </tr>

  <tr>

   <td width="336">      void remove ( const T&amp; x ); private:</td>

   <td width="189">// removes node with value x</td>

  </tr>

  <tr>

   <td width="336">          void insert ( Node &lt; T &gt;*&amp;, const T&amp; );</td>

   <td width="189">// private version of insert</td>

  </tr>

  <tr>

   <td width="336">          void remove ( Node &lt; T &gt;*&amp;, const T&amp; );</td>

   <td width="189">// private version of remove</td>

  </tr>

  <tr>

   <td width="336">      Node &lt; T &gt;* pred ( Node &lt; T &gt;* ); };</td>

   <td width="189">// returns predecessor of node</td>

  </tr>

  <tr>

   <td colspan="2" width="525"> </td>

  </tr>

 </tbody>

</table>

Where x is the target value for insert ( ) and remove ( ) functions. These <em>public </em>functions simply call their <em>private </em>versions.

The <em>private</em> versions of insert ( ) and remove ( ) functions can be implemented as <em>recursive</em> functions. When you implement the remove ( ) function, consider three possible cases: the node to be removed (1) is a leaf; (2) has only one child; and (3) has two children. In the first case, simply delete the node. In the second case, bypass the node making a new link from its parent to its child, and delete the node. In the third case, find the predecessor of the node – first move to the left child of the node, and then move to rightmost node in the tree, replace the value of the node with the value of its predecessor, delete the predecessor, and update the link to the deleted node, where the <em>private </em>non-recursive member function pred ( ) can be used to return the predecessor of a node.

To test your derived class, the source file of a driver program, prog7.cc, is supplied to you, which is in directory: ~cs340/progs/17f/p7. This program generates two sets of random integers in the range [ 0, R ] with R = 1000, and inserts these numbers of the first set in a vector of integers and the numbers of the second set in another vector of integers, and inserts the numbers of the first set in a binary search tree. The program searches for each number in the second vector in the binary search tree before and after the numbers in the second vector is removed from the tree. At the end, it prints the following values for the binary search tree: the number of nodes and the height of the tree. Finally, it prints the data values in the binary search tree in ascending order before and after the removals, since traversing a binary search tree inorder results a sorted list of values.




1

To get the size of a binary search tree, add the <em>public </em>and <em>private </em>versions of the size ( ) function in your binTree class with the prototypes unsigned size ( ) const and unsigned size ( Node &lt; T &gt;* ) const, respectively.




Put the implementation of your binary search tree class in a separate header file, say binSTree.h. Modified version of the class Node from the previous assignment includes the binTree and binSTree classes as <em>friends</em>, so the objects of these two classes can access the <em>private</em> members of the class Node. Include the header file Node.h in your header file binTree.h, and include the header file binTree.h in your header file binSTree.h. Make it sure that each header file is included only once, so the contents of each header file should be guarded as follows:




// include system header files using namespace std;




#ifndef a–const–value

#define a–const–value

// statements in the header file

#endif




For each header file, use a different const–value.




To compile and link the driver program with the system library routines, execute: Make N=7. To test your binary–search–tree class, execute: Make execute N=7. This command executes the driver program and displays the output as well as any error messages both on the terminal screen and in prog7.out. After you are done with the program, you don’t need its object and executable files any more. To delete them, execute: Make clean.




The correct output of this program is in file prog7.out, which is in the same directory with prog7.cc. If the program fails to generate the correct output, then to debug the program, copy the file prog7.cc in your own directory, uncomment some of the statements in that file, recompile and link the modified program, and then execute again.




<u>Note</u>: In <em>public</em> versions of insert ( ) and remove ( ), you’ll get compile errors when you pass the root as an argument to these functions. To eliminate compile errors, you need to pass the root as this–&gt;root.

When your program is ready, submit its header files to your TA by executing:

mail_prog.340 binTree.h binSTree.h.


