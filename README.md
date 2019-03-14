## Tobiko:

A companion software of [ikura](https://github.com/juugii/ikura) for the detection of rearranged TCR (and BCR) chains in single cell experiments. It has been primarily developed to detect productive rearranged TCR chains and assemble full receptors in Tab cells from 10x 3' sequenced libraries. It currently has limited support for other receptors (PR are welcome). Analysis typically takes 1h30, plus up to 5 hours for the rebarcoding of the sequencing files.

Tobiko requires data preprocessed with Ikura, as it takes its results folder as input.

## Getting Started

```bash
Tobiko v1.0
Usage: ./tobiko	[-n|--skip-rebarcoding] (optional, mostly for debugging)
		[-s|--specy] <specy:hs|HomoSapiens|mmu|MusMusculus>
		[-c|--chains] <anyof:IGH,IGL,IGK,TRA,TRB,TRG,TRD,IGH,IGL,IGK> (optional, default is TRA,TRB)
		[-i|--ikura] <ikuraOutputPath>
		[-u|--umithreshold] <threshold> (optional, default is 1)
		[-t|--threads] <coresNb> (optional, default is 16)

		Directory should be specified as absolute path.
```

Tobiko only requires to specify.

```bash
$ ./tobiko --specy HomoSapiens --ikura /path/to/nameOfSample
```

By default, Tobiko will use 16 cores, which has been found to be the best CPU/memory trade-off for a fast analysis. In the case of a lower configuration, Tobiko's resources can be limited (eg. with the option --threads 4).


## Prerequisites

Tobiko has been developed on Linux and tested on several 64-bits distribution (CentOS 7, Debian 9, Ubuntu 18.04 LTS), and should be compatible with MacOSX (Posix compliant).
It has the following dependencies: python>=3.6.5, R>=3.5.0 (with library ), umi_tools>=0.5.4, multiqc>=1.5.


## Installing

First, manually install [mixcr](https://mixcr.readthedocs.io/en/master/index.html) >= 2.1.12 on your system. You will also need to have R (>=3.5.0 preferred) and python>=3.6.5 installed.

For Tobiko to work out-of-the-box, all of these softwares should be directly callable, so add them to your environment path. *Alternatively*, you can edit manually the 'dependencies.txt' file to specify Tobiko custom paths and integrate it to your system. In case of any bad configuration, Tobiko will warn you.

Download and extract the [latest release of Tobiko](https://github.com/juugii/tobiko/releases/tag/v1.0.0), enter the directory and type:

```bash
$ make install

```

You will need administrative rights for this. You can also install Tobiko locally with:

```bash
$ make install PREFIX=/path/to/your/local/folder

```

You can then add the install folder in the path of your bashrc.


## Citation

Tobiko's article is under reviewing.
Tobiko relies on external tools, please cite:

[mixcr](https://mixcr.readthedocs.io/en/master/index.html): Dmitriy A. Bolotin, Stanislav Poslavsky, Alexey N. Davydov, Felix E. Frenkel, Lorenzo Fanchi, Olga I. Zolotareva, Saskia Hemmers, Ekaterina V. Putintseva, Anna S. Obraztsova, Mikhail Shugay, Ravshan I. Ataullakhanov, Alexander Y. Rudensky, Ton N. Schumacher & Dmitriy M. Chudakov. "Antigen receptor repertoire profiling from RNA-seq data." Nature Biotechnology 35, 908–911 (2017)

[UMItools](https://github.com/CGATOxford/UMI-tools): Smith, T., Heger, A., Sudbery, I., UMI-tools: modeling sequencing errors in Unique Molecular Identifiers to improve quantification accuracy. Genome Research.
