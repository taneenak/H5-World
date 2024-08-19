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
