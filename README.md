Download Link: https://assignmentchef.com/product/solved-me759-assignment-8
<br>
. In HW02 task3, you have implemented several different ways to carry out matrix multiplication in sequential computing. In this task, you will take the mmul function in HW02 that yields the best performance and parallelize it with OpenMP.

<ol>

 <li>Implement in a file called cpp the parallel version of the best-performing mmul function in HW02 task3 with the prototype defined as in matmul.h.</li>

 <li>Write a program cpp that will accomplish the following:

  <ul>

   <li>Create and fill with float type numbers the square matrices A and B (stored as 1D arrays in the order required by the best-performed mmul method, more details can be found in the description of HW02 task3). The dimension of A and B should be n×n where n is the first command line argument, see below.</li>

   <li>Compute the matrix multiplication <em>C </em>= <em>AB </em>using your parallel implementation with t threads where t is the second command line argument, see below.</li>

   <li>Print the first element of the resulting <em>C </em></li>

   <li>Print the last element of the resulting <em>C </em></li>

   <li>Print the time taken to run the mmul function in <em>milliseconds</em>.</li>

   <li>Compile: g++ task1.cpp matmul.cpp -Wall -O3 -o task1 -fopenmp</li>

   <li>Run (where n is a positive integer, t is an integer in the range [1, 20] ):</li>

  </ul></li>

</ol>

./task1 n t

<ul>

 <li>Example expected output:</li>

</ul>

1.0

1376.5

3.21

<ol>

 <li>On an Euler <em>compute node</em>:

  <ul>

   <li>Run task1 for value n = 1024, and value t = 1<em>,</em>2<em>,</em>·· <em>,</em>20. Generate a plot called task1.pdf which plots time taken by your mmul function vs. t in linear-linear scale.</li>

  </ul></li>

 <li>In HW02 task2, you’ve implemented the 2D convolution for sequential execution. In this task, you will use OpenMP to parallelize your previous implementation.

  <ol>

   <li>Implement in a file called cpp the parallel version of Convolve function with the prototype specified in convolution.h.</li>

   <li>Write a program cpp that will accomplish the following:

    <ul>

     <li>Create and fill with float-type numbers an n×n square matrix image (stored as a 1D array in row-major order), where n is the first command line argument, see below.</li>

     <li>Create a 3×3 mask matrix (stored in 1D in row-major order) of whatever mask values you like.</li>

     <li>Apply the mask matrix to the image using your Convolve function with t threads where t is the second command line argument, see below.</li>

     <li>Print the first element of the resulting output</li>

     <li>Print the last element of the resulting output</li>

     <li>Print the time taken to run the Convolve function in <em>milliseconds</em>.</li>

     <li>Compile: g++ task2.cpp convolution.cpp -Wall -O3 -o task2 -fopenmp</li>

     <li>Run (where n is a positive integer, t is an integer in the range [1, 20] ):</li>

    </ul></li>

  </ol></li>

</ol>

./task2 n t

<ul>

 <li>Example expected output:</li>

</ul>

2.0

137.5

3.21

<ol>

 <li>On an Euler <em>compute node</em>:

  <ul>

   <li>Run task2 for n = 1024, and t = 1<em>,</em>2<em>,</em>·· <em>,</em>20. Generate a figure called task2.pdf which plots the time taken by your Convolve function vs. t in linear-linear scale.</li>

   <li>Discuss your observations from the plot. Explain to what extent the increase in the number of threads improves the performance, and why the run time does not show significant decrease after reaching a certain number of threads.</li>

  </ul></li>

 <li>(<strong>Optional</strong>, Extra credits, 10 pts) There are ways to further improve the performance when using more threads (i.e. t <em>&gt; </em>10). For instance, the <em>data affinity </em>topic covered in class would be a good starting point to look into this.

  <ul>

   <li>Submit in a file task2 op.cpp that includes all necessary changes for improved scalability (there should be no need to change your Convolve function). Explain (if any) changes to the environment variables along with your discussions in c).</li>

   <li>On an Euler <em>compute node</em>, run task2 op for value n = 1024, and value t = 1<em>,</em>2<em>,</em>·· <em>,</em>20. Overlay this plot on the pattern you achieved in c) and save in a file task2 op.pdf.</li>

   <li>Discuss your observations from the plot.</li>

  </ul></li>

 <li>Implement a parallel merge sort<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> using OpenMP tasks.

  <ol>

   <li>Implement in a file called cpp the parallel merge sort algorithm with the prototype specified in msort.h. You may add other functions in your msort.cpp program, but you should not change the msort.h file. Your msort function should take an array of integers and return the sorted results in place in ascending order. For instance, after calling msort function, the original arr = [3, 7, 10, 2, 1, 3] would become arr = [1, 2, 3, 3, 7, 10].</li>

   <li>Write a program cpp that will accomplish the following:

    <ul>

     <li>Create and fill however you like with int type numbers an array arr with length n, where n is the first command line argument, see below.</li>

     <li>Apply your msort function to the arr. Set number of threads to t, which is the second command line argument, see below.</li>

     <li>Print the first element of the resulting arr</li>

     <li>Print the last element of the resulting arr</li>

     <li>Print the time taken to run the msort function in <em>milliseconds</em>.</li>

     <li>Compile: g++ task3.cpp msort.cpp -Wall -O3 -o task3 -fopenmp</li>

     <li>Run (where n is a positive integer, t is an integer in the range [1, 20], ts is the threshold as the lower limit to make recursive calls in order to avoid the overhead of recursion/task scheduling when the input array has small size; under this limit, a serial sorting algorithm without recursion calls will be used):</li>

    </ul></li>

  </ol></li>

</ol>

./task3 n t ts

<ul>

 <li>Example expected output:</li>

</ul>

1

513

3.21

<ol>

 <li>On an Euler <em>compute node</em>:

  <ul>

   <li>Run task3 for value n = 10<sup>6</sup>, value t = 8, and value ts = 2<sup>1</sup><em>,</em>2<sup>2</sup><em>,</em>·· <em>,</em>2<sup>10</sup>. Generate a plot called task3 ts.pdf which plots the time taken by your msort function vs. ts in linear-linear scale.</li>

   <li>Run task3 for value n = 10<sup>6</sup>, value t = 1<em>,</em>2<em>,</em>·· <em>,</em>20, and ts equals to the value that yields the best performance as you found in the plot of time vs. ts. Generate a plot called task3 t.pdf which plots time taken by your msort function vs. t in linear-linear scale.</li>

  </ul></li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> See the Parallel merge sort section in <a href="https://en.wikipedia.org/wiki/Merge_sort">this</a> link as a reference of the pseudo code.