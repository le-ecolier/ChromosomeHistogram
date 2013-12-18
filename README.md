Chromosome Location Histograms
=====


This is a brief R script to generate histograms of genomic locations broken out by chromosome, starting with a BED-like file containing chromosomal locations and intensity values. It sets axis limits equal to the sizes of the chromosomes (detecting human or mouse samples automatically based on the number of chromosomes), and graphs the results using [ggplot2][ggplot2] with [facet wrapping][facet wrapping]. For human data, it plots a vertical line at the location of the centromere for each chromosome. No vertical lines are plotted for mouse data, because all the chromosomes are telocentric so the centromeres are at the end. 

The intensity values could be peak height, fold change between samples, or any other measure of intensity at a given genomic location. In particular, a version of this script was used to generate Fig. S7 [(Bush et al.)][Bush], where the intensity is the fold change in H3K4me3 ChIP-seq peak size for all the peaks that are significantly changed by knocking out the gene H3f3b. Significantly changed peaks and fold changes were determined using [HOMER][HOMER] with the mouse mm9 genome. The script produces a graph for decreased peaks, but the data for increased peaks is also included in the repo so that the script can easily be modified to analyze this data as well. 

Sample output: 
-------

![Histogram](https://raw.github.com/biobonnie/ChromosomeHistogram/master/H3K4me3-downinKOpeaks.png)

These graphs are useful for detecting large-scale trends in genomic data, such as:
 - sequencing/mapping errors that lead to large portions of a chromosome having no reads mapped to it
 - Chip-seq peaks preferentially located near telomeres or centromeres
 - gross chromosomal abnormalities leading to no reads mapping to a region
 - overall changes in distribution of reads or peaks between two samples

Usage:
-----

*drawHist.sh*: Generates graphs of all files in the current directory with a "bed" extension, saving them as PNG files with the same name appended with "-graph.png". 

[ggplot2]: http://ggplot2.org
[facet wrapping]: http://wiki.stdout.org/rcookbook/Graphs/Facets%20(ggplot2)/
[Bush]: https://www.pubmedcentral.nih.gov/pmc/articles/PMC3635903/
[HOMER]: http://biowhat.ucsd.edu/homer/index.html