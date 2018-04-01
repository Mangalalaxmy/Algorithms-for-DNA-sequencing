# Algorithms-for-DNA-sequencing

This contains all the programming assignments for this course.

Week 1

In lecture and in a practical, we saw an implementation of the naive exact matching algorithm:

...and we saw a function that takes a DNA string and returns its reverse complement:

...and we saw a function that parses a DNA reference genome from a file in the FASTA format.

...and we saw a function that parses the read and quality strings from a FASTQ file containing sequencing reads.

First, implement a version of the naive exact matching algorithm that is strand-aware. That is, instead of looking only for occurrences of P in T, additionally look for occurrences of thereverse complement of P in T. If P is ACT, your function should find occurrences of both ACTand its reverse complement AGT in T.
If P and its reverse complement are identical (e.g. AACGTT), then a given match offset should be reported only once. So if your new function is called naive_with_rc, then the old naivefunction and your new naive_with_rc function should return the same results when P equals its reverse complement.
Hint: See this notebook for a few examples you can use to test your naive_with_rc function.
Next, download and parse the lambda virus genome, at: https://d28rh4a8wq0iu5.cloudfront.net/ads1/data/lambda_virus.fa

Week 2

In a practical, we saw Python code implementing the Boyer-Moore algorithm. Some of the code is for preprocessing the pattern P into the tables needed to execute the bad character and good suffix rules — we did not discuss that code. But we did discuss the code that performs the algorithm given those tables:

Measuring Boyer-Moore's benefit. First, download the Python module for Boyer-Moore preprocessing:
http://d28rh4a8wq0iu5.cloudfront.net/ads1/code/bm_preproc.py
This module provides the BoyerMoore class, which encapsulates the preprocessing info used by the boyer_moore function above. Second, download the provided excerpt of human chromosome 1:
http://d28rh4a8wq0iu5.cloudfront.net/ads1/data/chr1.GRCh38.excerpt.fasta
Third, implement versions of the naive exact matching and Boyer-Moore algorithms that additionally count and return (a) the number of character comparisons performed and (b) the number of alignments tried. Roughly speaking, these measure how much work the two different algorithms are doing.
For a few examples to help you test if your enhanced versions of the naive exact matching and Boyer-Moore algorithms are working properly, see these notebooks:
Naive
Boyer-Moore

Week 3

We saw how to adapt dynamic programming to find approximate occurrences of a pattern in a text. Recall that:

Rows of the dynamic programming matrix are labeled with bases from P and columns with bases from T
Elements in the first row are set to 0
Elements in the first column are set to 0, 1, 2, ..., as for edit distance
Other elements are set in the same way as elements of a standard edit distance matrix
The minimal value in the bottom row is the edit distance of the closest match between P and T
First, download the provided excerpt of human chromosome 1

https://d28rh4a8wq0iu5.cloudfront.net/ads1/data/chr1.GRCh38.excerpt.fasta

Second, parse it using the readGenome function we wrote before.

Third, adapt the editDistance function we saw in practical (copied below) to answer questions 1 and 2 below. Your function should take arguments p (pattern), t (text) and should return the edit distance of the match between P and T with the fewest edits.



Hint: In the "A new solution to approximate matching" video we saw that the best approximate match of P =GCGTATGCwithin T =TATTGGCTATACGGTThad 2 edits. You can use this and other small examples to double-check that your function is working.

