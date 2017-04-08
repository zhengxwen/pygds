pygds: Python Interface to CoreArray Genomic Data Structure (GDS) Files
===

![GPLv3](http://www.gnu.org/graphics/gplv3-88x31.png)
[GNU General Public License, GPLv3](http://www.gnu.org/copyleft/gpl.html)

[![Build Status](https://travis-ci.org/CoreArray/pygds.png)](https://travis-ci.org/CoreArray/pygds)


## Features

This package provides a high-level Python interface to CoreArray Genomic Data Structure (GDS) data files, which are portable across platforms with hierarchical structure to store multiple scalable array-oriented data sets with metadata information. It is suited for large-scale datasets, especially for data which are much larger than the available random-access memory. The pygds package offers the efficient operations specifically designed for integers of less than 8 bits, since a diploid genotype, like single-nucleotide polymorphism (SNP), usually occupies fewer bits than a byte. Data compression and decompression are available with relatively efficient random access.


## Package Maintainer

Dr. Xiuwen Zheng ([zhengxwen@gmail.com](zhengxwen@gmail.com))


## Installation

```sh
pip install git+git://github.com/CoreArray/pygds.git
```


## Citation

#### Original papers (implemented in R/Bioconductor):

[gdsfmt](http://bioconductor.org/packages/gdsfmt), [SeqArray](http://bioconductor.org/packages/SeqArray)

Zheng X, Levine D, Shen J, Gogarten SM, Laurie C, Weir BS (2012). A High-performance Computing Toolset for Relatedness and Principal Component Analysis of SNP Data. *Bioinformatics*. [DOI: 10.1093/bioinformatics/bts606](http://dx.doi.org/10.1093/bioinformatics/bts606).

Zheng X, Gogarten S, Lawrence M, Stilp A, Conomos M, Weir BS, Laurie C, Levine D (2017). SeqArray -- A storage-efficient high-performance data format for WGS variant calls. *Bioinformatics*. [DOI: 10.1093/bioinformatics/btx145](http://dx.doi.org/10.1093/bioinformatics/btx145).



## Examples

```Python
import pygds as gds

fn = get_example_path('ceu_exon.gds')
f = gds.gdsfile()
f.open(fn)
f.show()
f.close()
```

```
File: pygds/data/ceu_exon.gds
+    [  ] *
|--+ description   [  ] *
|--+ sample.id   { Str8 90 LZMA_ra(35.8%), 258B } *
|--+ variant.id   { Int32 1348 LZMA_ra(16.8%), 906B } *
|--+ position   { Int32 1348 LZMA_ra(64.6%), 3.4K } *
|--+ chromosome   { Str8 1348 LZMA_ra(4.63%), 158B } *
|--+ allele   { Str8 1348 LZMA_ra(16.7%), 902B } *
|--+ genotype   [  ] *
|  |--+ data   { Bit2 1348x90x2 LZMA_ra(26.3%), 15.6K } *
|  |--+ ~data   { Bit2 90x1348x2 LZMA_ra(29.3%), 17.3K }
|  |--+ extra.index   { Int32 0x3 LZMA_ra, 19B } *
|  \--+ extra   { Int16 0 LZMA_ra, 19B }
|--+ phase   [  ]
|  |--+ data   { Bit1 1348x90 LZMA_ra(0.91%), 138B } *
|  |--+ ~data   { Bit1 90x1348 LZMA_ra(0.91%), 138B }
|  |--+ extra.index   { Int32 0x3 LZMA_ra, 19B } *
|  \--+ extra   { Bit1 0 LZMA_ra, 19B }
|--+ annotation   [  ]
|  |--+ id   { Str8 1348 LZMA_ra(38.4%), 5.5K } *
|  |--+ qual   { Float32 1348 LZMA_ra(2.26%), 122B } *
|  |--+ filter   { Int32,factor 1348 LZMA_ra(2.26%), 122B } *
|  |--+ info   [  ]
|  |  |--+ AA   { Str8 1348 LZMA_ra(25.6%), 690B } *
|  |  |--+ AC   { Int32 1348 LZMA_ra(24.2%), 1.3K } *
|  |  |--+ AN   { Int32 1348 LZMA_ra(19.8%), 1.0K } *
|  |  |--+ DP   { Int32 1348 LZMA_ra(47.9%), 2.5K } *
|  |  |--+ HM2   { Bit1 1348 LZMA_ra(150.3%), 254B } *
|  |  |--+ HM3   { Bit1 1348 LZMA_ra(150.3%), 254B } *
|  |  |--+ OR   { Str8 1348 LZMA_ra(20.1%), 342B } *
|  |  |--+ GP   { Str8 1348 LZMA_ra(24.4%), 3.8K } *
|  |  \--+ BN   { Int32 1348 LZMA_ra(20.9%), 1.1K } *
|  \--+ format   [  ]
|     \--+ DP   [  ] *
|        |--+ data   { Int32 1348x90 LZMA_ra(25.1%), 118.8K } *
|        \--+ ~data   { Int32 90x1348 LZMA_ra(24.1%), 114.2K }
\--+ sample.annotation   [  ]
   \--+ family   { Str8 90 LZMA_ra(57.1%), 222B }
```
