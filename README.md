# PVDP 1.0 Manual

1. [Introduction](#Introduction)  
   1.1. [Supported files](#supported)  
   1.2. [Pipeline](#Pipeline)  
   1.3. [Performance](#Performance)
   
2. [Installation](#Installation)  
   2.1. [Prerequisites](#Prerequisites)   
   2.2. [Downloading project](#Download)
  
3. [Tutorial](#Tutorial)  

4. [Support or contact](#Support)

<a name="Introduction"></a>
### Introduction

The low yields of many crops around the world are explained, among other aspects, by the lack of good phytosanitary management practices in addition to the widespread use of planting material not certified for its viral health. The use of next generation sequencing (NGS) has allowed the complete or partial characterization of a significant number of viral variants that infect crops in different regions of the world.

This tool was carried out in order to strengthen the programs of genetic improvement, quarantine surveillance and certification of planting material. This package is free to use and is specific for the diagnosis of viruses in plants. 

<a name="supported"></a>
### Supported files

The current version supports paired-end reads and unpaired reads, products of massively parallel sequencing technology [NGS](https://www.illumina.com/science/technology/next-generation-sequencing.html). The files can be in two formats essentially:

- FASTQ or FASTQ.GZ:  

>@seq_ID                              [1]
>
>CTCAGCTAAATACTTTGACACCNGTANNANNNN    [2]
> 
> \+                                  [3]
>
>BBDEBDDDDHHHHFHEEEEEEEE#3AC#####   [4]

FASTQ file is composed of four lines. [1] This line includes a unique ID and information such as flow cell lane information. [2] This line includes the nucleotides of the sequence. [3] A separator item (+). [4] This line includes quality values about sequences; this quality is denominated Phred Score and is described in ASCII symbols, every simbol has a respective number asociated and a higher number signifies higher acurracy of each nucleotide.

- FASTA

> \>seq_ID                            [1]
>
>ACTGCTCGACGATGACTGCATGCTGCACTGTCA    [2]

FASTA file is composed of two lines. [1] This line includes a unique ID. [2] This line includes the nucleotides of the sequence.

<a name="Pipeline"></a>
### Pipeline

![Pipeline](/images/pvdp_pipeline.png)

<a name="Performance"></a>
### Performance

The following results were obtained by performing the analysis on an Intel Core i5 9500 CPU @ 3.00 GHz * 6, 16 GB RAM, using the package of python [Memory Profiler](https://pypi.org/project/memory-profiler/).

| Data set | Disk space (MB) | Time (m) | Peak RAM usage (GB) | Additional disk space required (MB) |  
| :---: | :---: | :---: | :---: | :---: |
| rna_physalis_peruviana.fastq (paired) | 54 | 5.8 | 2.62 | 17.6 |

![Memory Profile](/images/memory_profile_physalis.png)


| Data set | Disk space (MB) | Time (m) | Peak RAM usage (GB) | Additional disk space required (MB) |  
| :---: | :---: | :---: | :---: | :---: |
| rna_solanum_phureja.fastq.gz | 1848 | 144 | 2 | 473.3 |

![Memory Profile](/images/memory_profile_phureja.png)

Additionally, the execution time and the maximum peak of ram were evaluated for a set of NGS data obtained from leaf tissue of physalis peruviana. Seven data sizes were evaluated, each interval was one million reads. The following graphs summarize the information obtained:

![Memory Profile](/images/time_physalis.png)

![Memory Profile](/images/peak_physalis.png)


<a name="Installation"></a>
### Installation

Sequence alignment is done through BLAST, the algorithms for automatic execution and filtering are written in Python. It is possible to interpret the result tables to generate a graphic report using Rproject and RStudio.

<a name="Prerequisites"></a>
### Prerequisites

**1. BLAST**

Please go to official [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=Download) page and install the correct version for you operative system. To verify that the tool works correctly, enter the command terminal and type: *blastn*

The installation was successful if you get the following message:

```markdown
BLAST query/options error : Either a BLAST database or subject sequence(s) must be specified
Please refer to the BLAST+ user manual.
```

**2. Python**

Please go to official [Python](https://www.python.org/downloads/) page and install the correct version (3.7+) for you operative system. To verify that the tool works correctly, enter the command terminal and type: *python --version*

The installation was successful if you get the following message:

```markdown
Python 3.7 (or superior)
```

**3. R project**

To download [R project](https://cran.r-project.org/mirrors.html) please choose your preferred CRAN mirror in the official page and then select the correct version for you operative system.

**4. RStudio**

It is necessary to have R project installed before this step. Please go to official [RStudio](https://rstudio.com/products/rstudio/download/) page and install the correct version for you operative system. To verify that the tool works correctly, run the program. 

Additional the following packages need to be installed

```markdown
- ggplot2
- RColorBrewer
- dplyr
- knitr
- rworldmap
```
To verify that the graphing section is working correctly download the consolidation of [result tables](https://github.com/biotecnologiamicrobianaunalmed/Plant-Virus-Detection-Package/blob/master/results_rna_physalis_peruviana.zip). Then open RStudio, configure the working directory correctly and specify the path in which the main file (***List_of_tables_rna_physalis_peruviana_1_rna_physalis_peruviana_2_nr.tsv***) is located.

![Specify Path](/images/specify_path.png)

Then run the program and view the generated file. 

![Run All](/images/run_all.png)

![Preview](/images/preview.png)

This file can be opened in the browser and saved by pressing print.

The generated report looks as follows:

![Viral Result](/images/vr1.png)

![Viral Result](/images/vr2.png)

![Viral Result](/images/vr3.png)

![Viral Result](/images/vr4.png)

![Viral Result](/images/vr5.png)

<a name="Download"></a>
### Download

The package is distributed as follows:

```markdown
----->bin
       >identifyPlantVirusesV2.py
       >virusBLASTv2.py
       >nonRedundantSequencesV3.py
       >identification_of_virus_species_V2.py
       >identificacion_of_distant_viruses_V1.py
       >genomeBLASTV2.py
       >outputTables.py
       >graphing.Rmd
----->db
       >PlantVirusesDB.nhr
       >PlantVirusesDB.nin
       >PlantVirusesDB.nsq
       >FalsePositives.nhr
       >FalsePositives.nin
       >FalsePositives.nsq
----->info
       >license.txt
```

The whole package can be downloaded in its compressed version [PVDP.zip](https://github.com/MicrobialBiotechnologyLaboratory/Virus-Detection-Package/blob/master/pvdp.zip). 

***The last update of the viral database was made on October 25, 2019.***

<a name="Tutorial"></a>
### Tutorial

To perform this tutorial please download the [test files](https://github.com/biotecnologiamicrobianaunalmed/Plant-Virus-Detection-Package/blob/master/test_files_rna_physalis_peruviana.zip) that are available in the repository. Unzip the files and locate them in the package folder.

![Structure](/images/main_folder.png)

First open the command terminal and go to the folder where the downloaded files are located. The main script is called ***identifyPlantVirusesV2.py***. In order to access to the help copy the following line of text into the terminal:

```markdown
python3 ./bin/identifyPlantVirusesV2.py --help
```
You must obtain the following information:

```markdown
usage: identifyPlantVirusesV2.py [-h] -seq1 SEQ1 [-seq2 SEQ2] [-hostdb HOSTDB]
                                 [-num_threads NUM_THREADS] [-append] [-o O]
                                 [-subset SUBSET] [-ra] [-top TOP]
                                 [-threshold THRESHOLD] [-filtering_db]

optional arguments:
  -h, --help            show this help message and exit
  -seq1 SEQ1            path to sequence file 1 in fastq or fasta format
  -seq2 SEQ2            path to sequence file 2 in fastq or fasta format
  -hostdb HOSTDB        path to custom filtering DB or default DBs: Potato,
                        Gulupa or CapeGooseberry
  -num_threads NUM_THREADS
                        number of processors to use during BLAST searches
  -append               create filtered sequence files progressively. Slow but
                        requires less RAM
  -o O                  basename of output directory and files
  -subset SUBSET        use the specified number of reads for analysis
  -ra                   do not include reads with ambiguous base calls
  -top TOP              use only the most abundant non redundant reads for
                        analysis
  -threshold THRESHOLD  exclude non redundant reads below the specified
                        sequence count
  -filtering_db         uses custom filtering_db
```

To run the program the minimum requirement is to give the path to at least one of the files, that is:

```markdown
python3 ./bin/identifyPlantVirusesV2.py -seq1 /home/user/Documents/rna_physalis_peruviana_1.fastq  
```

Then press enter and please be patient. The program displays messages in the terminal to inform about the step it is in. To visualize the results, follow the steps mentioned in the RStudio section.

<a name="Support"></a>
### Support or Contact

Having troubles? Please contact us.
