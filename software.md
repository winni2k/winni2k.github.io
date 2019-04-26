---
title: Software
---
## abeona

[Abeona]() is an experimental transcriptome assembler based on the [cortexpy](.#Cortexpy) library and [kallisto](https://pachterlab.github.io/kallisto/). 

## cortexpy

[Cortexpy](https://github.com/winni2k/cortexpy) is a python package for inspecting, traversing, and manipulating colored and linked De Bruijn graphs in [Cortex](https://github.com/iqbal-lab/cortex)/[Mccortex](https://github.com/mcveanlab/mccortex) format. A special thanks to Kiran V Garimella who was instrumental in helping me get this project off the ground and for laying the groundwork with his own Cortex library [CortexJDK](https://github.com/mcveanlab/CortexJDK).

## Visual cortex

[Visual cortex](https://github.com/winni2k/visual_cortex) is a collection of HTML, CSS, and JavaScript that I use to visualize small, multi-color transcript De Bruijn graphs that I create using cortexpy. 

![a_visual_cortex_example](https://www.frontiersin.org/files/Articles/408314/fpls-09-01625-HTML/image_m/fpls-09-01625-g002.jpg)

## dmpy

[Dmpy](https://github.com/kvg/dmpy) is a domain-specific language for writing GNU Make files from inside python. It is a port of the perl package [DistributedMake]()

## GLPhase

GLPhase is a CUDA-enabled haplotype phasing and imputation tool for tens of thousands of low coverage sequencing samples.  GLPhase was developed for the [Haplotype Reference Consortium](http://www.haplotype-reference-consortium.org/).  The GLPhase source code is available [here](https://github.com/winni2k/GLPhase).

## DistributedMake

[DistributedMake](https://github.com/winni2k/DM) is a domain-specific language for writing GNU Make files from inside perl. First created by Kiran V Garimella during his first tour at the Broad Institute, it was further developed by Kiran and me during our time at the Wellcome Trust Centre for Human Genetics. 

_Long live the semi-colon ..._
```perl
#!/usr/bin/env perl -w
use strict;
use DM;
my @args = (dryRun => 0, numJobs=>100, engineName => 'localhost');
my $dm = DM->new(@args);    

for my $val (1..100){
    $dm->addRule(
        "hello_world_$val",
        "",
        "echo $val; sleep 5; echo ".($val + 100)."; touch hello_world_$val"
    );
}
$dm->execute();
```

