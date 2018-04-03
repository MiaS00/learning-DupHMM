# learning-DupHMM

What is DupHMM?
DupHMM is an application which identifies copy number variations given only a SAM file of reads mapped to a reference genome. This is accomplished by breaking up each chromosome into 'windows' of a certain size and determining what the most likely copy number value for each window is, a process described in detail below.

Designed to be simple to use, a typical DupHMM run only involves four command-line options: one designating the location of the SAM file, one designating the output directory, one designating the CNV values (e.g. single copy, double copy, deleted, etc.) which you wish to find, and one designating a window binning size. Other options are available, but these four will likely be the only ones you will need

How does it work?
So how does DupHMM work? It works under the assumption that most of the chromosome being examined is not duplicated and that the duplications being sought after are rare events. Starting with this assumption, it breaks up a chromosome into user-specified bins or 'windows' (identified as black bars in the screenshot below) and counts up the number of reads mapping per window. A histogram of the number of reads mapping per window is then created, and a Poisson distribution is fit to this histogram:

