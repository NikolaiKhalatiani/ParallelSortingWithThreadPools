# Parallel Sorting
<p>In this exercise you should parallelize the Mergesort sorting algorithm learned from the lecture.
For that, a <a rel="noopener noreferrer" href="https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/util/concurrent/ForkJoinPool.html">ForkJoinPool</a> from the standard library can be used.</p>

## Benchmark
<p>The <code>BenchmarkApproaches</code> class is already included in the template. The execution of the contained <code>main</code> method performs a benchmark of the three mergesort implementations.
If you have not yet implemented all versions, you can simply comment out the relevant benchmark.</p>
<p>The benchmarks do not test the implementation for correctness, but only measure the time that is required for execution!</p>
<p>For the benchmarks you should import the project as a Maven project, for this you have to do the following: <br>
Eclipse: Simply import the project as a Maven project <br>
IntelliJ: After the first import, do this: Shift + Ctrl + A -&gt; Reimport all Maven Projects <br></p>

## Classes
<p>You should implement two different variants of the algorithm and then compare them with a sequential variant.
The sequential variant is already implemented in the template, as are the methods of the classes <code>ParallelMergeSort</code> and<code>BetterParallelMergeSort</code>.</p>
<p>In order to be able to use a <code>ForkJoinPool</code>, your classes have to implement the abstract class<code>RecursiveAction</code> and the abstract method <code>compute</code>. Within the <code>compute</code> class you can use<code>invoke</code> and <code>invokeAll</code> to start the execution of further<code>RecursiveActions</code>, which are then executed by the <code>ForkJoinPool</code>.</p>
<ol><li><strong>ParallelMergeSort</strong><br>
Complete the class <code>ParallelMergeSort</code>. Every time the array is split into two sub-arrays, the class should submit two tasks to the <code>ForkJoinPool</code>.
As soon as your implementation is finished and the public correctness test is successful, test the performance and compare it with the sequential solution!</li>
<li><strong>BetterParallelMergeSort</strong><br>
You should have noticed that <code>ParallelMergeSort</code> is significantly slower than the sequential solution.
This is because we are creating new tasks for sorting very small arrays too, and this involves a lot of overhead.
A parallel mergesort implementation that is supposed to achieve better performance should therefore create fewer tasks during execution.
Complete the class <code>BetterParallelMergeSort</code>, which sorts arrays that are below a certain size sequentially.
<p>You should then empirically determine the boundary between parallel and sequential execution.
Try different values ​​for this. Try to find a value that executes fastest for an array of 100,000 elements!</p>
<p>The values ​​can vary depending on the hardware, operating system and other factors. So there is no one-stop solution here!</p></li>
</ol>
