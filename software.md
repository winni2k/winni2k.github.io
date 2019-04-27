---
title: Software
---
## abeona

[Abeona]() is an experimental transcriptome assembler based on the [cortexpy](./software.md#cortexpy) library and [kallisto](https://pachterlab.github.io/kallisto/). In [this paper](https://doi.org/10.3389/fpls.2018.01625) we use abeona to reconstruct and 
[visualize](./software.md#visual-cortex) transcript isoforms of DAL19 in Norway spruce.

## cortexpy

[Cortexpy](https://github.com/winni2k/cortexpy) is a python package for inspecting, traversing, and manipulating colored and linked De Bruijn graphs in [Cortex](https://github.com/iqbal-lab/cortex)/[Mccortex](https://github.com/mcveanlab/mccortex) format. A special thanks to [Kiran V Garimella](https://github.com/kvg) who was instrumental in helping me get this project off the ground and for laying the groundwork with his own Cortex library [CortexJDK](https://github.com/mcveanlab/CortexJDK).

## Visual Cortex

[Visual cortex](https://github.com/winni2k/visual_cortex) is a collection of HTML, CSS, and JavaScript that I use to visualize small, multi-color transcript De Bruijn graphs that I create using [cortexpy](./software.md#cortexpy). 

<a href="https://www.frontiersin.org/articles/10.3389/fpls.2018.01625/full#F2">
    <img src="/assets/img/visual_cortex.jpg" alt="a_visual_cortex_example">
</a>

## dmpy

[Dmpy](https://github.com/kvg/dmpy) is a python port of [DistributedMake](./software.md#DistributedMake). It's friendlier on the eyes than DistributedMake...

_Where have all the semi-colons gone?_
```python
from dmpy import DistributedMake, get_dm_arg_parser

m = DistributedMake(args_object=get_dm_arg_parser().parse_args())

m.add("test_output_file", None, "echo 'hi world'")
m.execute()
```

## GLPhase

GLPhase is a CUDA-enabled haplotype phasing and imputation tool for tens of thousands of low-coverage sequencing samples.  GLPhase was developed for the [Haplotype Reference Consortium](http://www.haplotype-reference-consortium.org/).  The GLPhase source code is available [here](https://github.com/winni2k/GLPhase), and our paper describing the method is available [here](https://doi.org/10.1038/ng.3643).

## hapfuse

[Hapfuse](https://bitbucket.org/wkretzsch/hapfuse/overview) is a fast haplotype ligation tool designed primarily to work with haplotypes in [Binary Call Format](http://samtools.github.io/hts-specs/BCFv1_qref.pdf), although other formats are supported. Hapfuse is an extension of the hapfuse code written by Yi Wang for the [SNPTools package](https://www.hgsc.bcm.edu/software/snptools). Hapfuse has been used to ligate haplotypes phased in overlapping blocks in conjunction with [GLPhase](https://doi.org/10.1038/ng.3643) and with [SHAPEIT3](https://biobank.ctsu.ox.ac.uk/crystal/docs/impute_ukb_v1.pdf).

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

