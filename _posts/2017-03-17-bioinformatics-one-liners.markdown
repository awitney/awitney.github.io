---
layout: default
title:  "Bioinformatics one liners"
date:   2017-03-17
categories: jekyll update
---

#### Counting the number of reads in a fastq file:

{% highlight bash %}
for i in *.fastq.gz; do echo $i $(($(zcat $i | wc -l) / 4)); done
{% endhighlight %}

#### Get average coverage for bam alignment:

{% highlight bash %}
samtools depth -a <bam file> |  awk '{sum+=$3} END { print "Average = ",sum/NR}'
{% endhighlight %}

Alternatively:

{% highlight bash %}
samtools depth -a <bam file> | cut -f3 | perl -lane '$a+=$_ for (@F);$f+=scalar(@F);END{print "ave: ".$a/$f}'
{% endhighlight %}



