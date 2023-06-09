Download Link: https://assignmentchef.com/product/solved-cs2110-homework7-subroutines
<br>
In this assignment, you will be implementing several subroutines in assembly, taking advantage of the calling convention that has been outlined in class/lecitation. <strong>For each subroutine, you will be required to implement the entire calling convention. This includes the buildup and teardown on the stack</strong>.

<a name="_Toc5756"></a>  Instructions

You have been provided three assembly files, <strong>string ops.asm, handshake.asm, and buildheap.asm</strong>. These files contain a label for each of the subroutines that you will be asked to implement. <strong>DO NOT RENAME THE LABELS! </strong>You can add more to suit your needs, but don’t change the existing ones. Implement the following subroutines, use complx to debug them, and submit your files on Gradescope.

It is in your best interest to do the problems in order. The last one builds on the first two.

<a name="_Toc5757"></a> Part 1: String Operations

The first part of this assignment is to implement a method to count the occurrences of a character in a string. This will utilize the strlen subroutine, which has been implemented for you.

<h3><a name="_Toc5758"></a>1.1.1         String Length</h3>

To help you get started on the homework, we have provided you with the implementation of strlen. It includes the buildup of the stack, body of the function, and teardown of the stack. The pseudocode is provided here for your reference, but <strong>you do not have to implement this yourself</strong>. You will, however, have to call it from the next subroutine, so make sure you are familiar with how it works.

<h4>Pseudocode</h4>

int strlen(String s) { int count = 0; while (s.charAt(count) != “ ”) { count++;

}

}

<h3><a name="_Toc5759"></a>1.1.2         Count Character</h3>

Complete the count occurrence function in the string ops.asm file. This function should count how many times a given character appears in a string. This method should call the strlen method that you implemented in the previous part.

<strong>Pseudocode</strong>

int count_occurrence(String s, char c) { int count = 0; for (int i = 0; i &lt; strlen(s); i++) { if (s.charAt(i) == c) { count++;

}

} return count;

}

<h2><a name="_Toc5760"></a>1.2         Part 2: Handshaking</h2>

The second part of this assignment is solving the handshake problem.

<h4>Background</h4>

With n people at a party, find the maximum number of handshakes possible given that any two people can only shake each other’s hand once. This problem can be easily solved using recursion and the pseudocode for this problem is in the next section!

<h4>Pseudocode</h4>

int handshake(int n) { if (n == 0)

return 0;

else return (n – 1) + handshake(n – 1);

}

<h2><a name="_Toc5761"></a>1.3         Part 3: Build Heap</h2>

<strong>Background</strong>

If you have taken CS 1332 (don’t worry if you haven’t), then you might be familiar with the data structure known as the binary heap. A binary heap (<strong>specifically a max heap</strong>) is essentially a binary tree with the property that for every node, its children are less than or equal to it. This means that the root node of the heap is the largest element. The cool thing about binary heaps is that they can be represented as arrays, where a node at index n has its left child at index 2n + 1 and its right child at index 2n + 2. The goal of the next two problems will be to implement a function that will order an array of elements so that they form a valid heap. While it may help you to know more about binary heaps in order to understand what is going on

(you can ready about them at <a href="https://www.geeksforgeeks.org/binary-heap/">https://www.geeksforgeeks.org/binary-heap/</a><a href="https://www.geeksforgeeks.org/binary-heap/">)</a>, you don’t actually have to know anything about them since we give you the pseudocode.

<h3><a name="_Toc5762"></a>1.3.1         Heapify</h3>

The first subroutine that we will have you implement is heapify. Heapify takes in an array, its length, and a given node i and then ensures that the heap property of a node being larger than its children is maintained for that node. If you have to swap two elements, then heapify recursively re-checks the heap property for child nodes. Once we have implemented, we will be able to call it for every node to actually convert a given array into a heap.

Your job is to implement heapify in the buildheap.asm file, starting at the heapify label.

<h4>Heapify Pseudocode</h4>

void heapify(int[] arr, int n, int i) {

// The following are all indices, not values

int largest = i; // Initialize largest as root int leftChild = 2*i + 1; // left = 2*i + 1 int rightChild = 2*i + 2; // right = 2*i + 2

// If left child is larger than root if (leftChild &lt; n &amp;&amp; arr[leftChild] &gt; arr[largest]) largest = leftChild;

// If right child is larger than largest so far if (rightChild &lt; n &amp;&amp; arr[rightChild] &gt; arr[largest]) largest = rightChild;

// If largest is not root if (largest != i)

{ swap(arr[i], arr[largest]);

// Recursively heapify the affected sub-tree heapify(arr, n, largest);

}

}

<h3><a name="_Toc5763"></a>1.3.2         Build Heap (15 points)</h3>

Once you’ve implemented heapify, buildheap is easy. All you have to do is start at the end of the array and iterate backwards over each element, calling heapify on each one.

In buildheap.asm, implement the following pseudocode, starting at the buildheap label.

<h4>Build Heap Pseudocode</h4>

void buildheap(int arr[], int n) { for (int i = n; i &gt;= 0; i–) heapify(arr, n, i);

}

<h1><a name="_Toc5764"></a>2           Deliverables</h1>

Please upload the following files onto the assignment on Gradescope:

<ol>

 <li>string ops.asm</li>

 <li>asm</li>

 <li>asm</li>

</ol>

<strong>Be sure to check your score to see if you submitted the right files, as well as your email frequently until the due date of the assignment for any potential updates.</strong>

<h1><a name="_Toc5765"></a>3           LC-3 Assembly Programming Requirements</h1>

<h2><a name="_Toc5766"></a>3.1         Overview</h2>

<ol>

 <li>Your code must assemble with <strong>NO WARNINGS OR ERRORS</strong>. To assemble your program, open the file with Complx. It will complain if there are any issues. <strong>If your code does not assemble you WILL get a zero for that file.</strong></li>

 <li><strong>Comment your code! </strong>This is especially important in assembly, because it’s much harder to interpret what is happening later, and you’ll be glad you left yourself notes on what certain instructions are contributing to the code. Comment things like what registers are being used for and what less intuitive lines of code are actually doing. To comment code in LC-3 assembly just type a semicolon (;), and the rest of that line will be a comment.</li>

 <li>Avoid stating the obvious in your comments, it doesn’t help in understanding what the code is doing.</li>

</ol>

<h4>Good Comment</h4>

<table width="404">

 <tbody>

  <tr>

   <td width="167">ADD R3, R3, -1</td>

   <td width="237">; counter–</td>

  </tr>

  <tr>

   <td width="167">BRp LOOP<strong>Bad Comment</strong></td>

   <td width="237">; if counter == 0 don’t loop again</td>

  </tr>

  <tr>

   <td width="167">ADD R3, R3, -1</td>

   <td width="237">; Decrement R3</td>

  </tr>

  <tr>

   <td width="167">BRp LOOP</td>

   <td width="237">; Branch to LOOP if positive</td>

  </tr>

 </tbody>

</table>

<ol start="4">

 <li><strong>DO NOT assume that ANYTHING in the LC-3 is already zero. </strong>Treat the machine as if your program was loaded into a machine with random values stored in the memory and register file.</li>

 <li>Following from 3. You can randomize the memory and load your program by doing File – Randomize and Load.</li>

 <li>Use the LC-3 calling convention. This means that all local variables, frame pointer, etc… must be pushed onto the stack. Our autograder will be checking for correct stack setup.</li>

 <li>Start the stack at xF000. <strong>The stack pointer always points to the last used stack location. </strong>This means you will allocate space <strong>first</strong>, then store onto the stack pointer.</li>

 <li>Do NOT execute any data as if it were an instruction (meaning you should put .fills after <strong>HALT </strong>or RET).</li>

 <li>Do not add any comments beginning with @plugin or change any comments of this kind.</li>

 <li><strong>Test your assembly. </strong>Don’t just assume it works and turn it in.</li>

</ol>

<h2><a name="_Toc5767"></a>3.2         LC-3 Calling Convention Guide</h2>

A handy assembly guide written by Kyle Murray (RIP) follows on the next page:














