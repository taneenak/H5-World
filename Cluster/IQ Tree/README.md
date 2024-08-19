# IQ Tree 
```auspiceMainDisplayMarkdown
#!/bin/bash

#SBATCH --job-name=IQ_tree
#SBATCH --partition=gpu_p
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=2
#SBATCH --mem=2G
#SBATCH --time=7-00:00:00
#SBATCH --output=%x_%j.out
#SBATCH --error=%x_%j.err
#SBATCH --mail-user=xxx.edu
#SBATCH --mail-type=END,FAIL    # Mail events (NONE, BEGIN, END, FAIL, ALL)

cd $SLURM_SUBMIT_DIR

ml IQ-TREE/2.3.5-Linux 
iqtree2 -s xxx.fasta --date TAXNAME -m TEST --alrt 1000 -B 1000 --date-ci 100 -nt AUTO 
```

# Notes
--date TAXNAME 
Extract dates from taxon names after last '|'

-alrt:
specifies the number of bootstrap replicates for SH-aLRT where 1000 is the minimum number recommended.
Specify number of replicates (>=1000) to perform SH-like approximate likelihood ratio test (SH-aLRT) (Guindon et al., 2010)

--date-ci NUM
Number of replicates to compute confidence interval

UFBoot:
-B specifies the number of bootstrap replicates where 1000 is the minimum number recommended. The section MAXIMUM LIKELIHOOD TREE in example.phy.iqtree shows a textual representation of the maximum likelihood tree with branch support values in percentage. The NEWICK format of the tree is printed to the file example.phy.treefile. In addition, IQ-TREE writes the following files:
example.phy.contree: the consensus tree with assigned branch supports where branch lengths are optimized on the original alignment.
example.phy.splits.nex: support values in percentage for all splits (bipartitions), computed as the occurence frequencies in the bootstrap trees. This file can be viewed with the program SplitsTree to explore the conflicting signals in the data. So it is more informative than consensus tree, e.g. you can see how highly supported the second best conflicting split is, which had no chance to enter the consensus tree.
example.phy.splits (if using -wsplits option): This file contains the same information as example.phy.splits.nex but in star-dot format.

-nt:
Specify the number of CPU cores for the multicore version. A special option -nt AUTO will tell IQ-TREE to automatically determine the best number of cores given the current data and computer.

