Installing Séance
=================

Séance builds on multiple applications and python libraries to provide a complete analysis pipeline from raw data to visualisation. The easiest way to install Séance is to install the python code first, followed by the application dependencies as there is a handy subcommand to check your installation.

[Installation of Python source](#installation-of-python-source)  
[External tools](#external-tools)

   
[Back to Séance home](../README.md)

### Installation of Python source

Get the source distribution, untar it and cd into it:

```
wget https://github.com/ariloytynoja/seance/raw/main/files/Seance-0.12.tar.gz
tar xf Seance-0.12.tar.gz
cd Seance-0.12/
```

One of the python modules requires libffi, which is not handled by pip properly (at time of writing). The workaround for Ubuntu/Debian is to just install it manually using apt:  
 

```
sudo apt-get install libffi-dev
```

Next use the setup script to install the Séance module, the main Séance application script and all python dependencies (everything assumes you are running Python 2.7.x):

```
sudo python setup.py install
```

If all went well, you should be able to run:

```
seance test
```

Here is an example of what you should see:

```
ajm@leviathan:~/Seance-0.12$ seance test
checking system for cluster command dependancies :
    pagan found.
    blastn (needed for --label) not found!

checking system for phylogeny command dependancies :
    pagan found.
    exonerate found.
    bppphysamp not found!

checking system for preprocess command dependancies :
    uchime (needed for --chimeras) not found!
    sff2fastq found.
    PyroDist (needed for --denoise) not found!
    FCluster (needed for --denoise) not found!
    PyroNoise (needed for --denoise) not found!
```

From here you must install any missing dependencies that you need.

* * *

### External tools

Mandatory dependencies:

*   [PAGAN](https://ariloytynoja.github.io/pagan-msa/ "Pagan")
*   [Exonerate](https://www.ebi.ac.uk/about/vertebrate-genomics/software/exonerate "Exonerate")
*   bppphysamp (distributed with PAGAN)
*   [BLAST+](https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ "BLAST")

Optional dependencies:

*   [Ampliconnoise](https://code.google.com/p/ampliconnoise/downloads/list "AmpliconNoise") (if using the –denoise option)
*   [sff2fastq](https://github.com/indraniel/sff2fastq/ "sff2fastq") (needed for raw 454 data)
*   [UCHIME](http://drive5.com/uchime/uchime_download.html "UCHIME") (if using the –chimeras option)