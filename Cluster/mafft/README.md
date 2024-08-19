# Align 

```auspiceMainDisplayMarkdown
#!/bin/bash
#SBATCH --job-name=j_MAFFT
#SBATCH --partition=batch
#SBATCH --mail-type=ALL
#SBATCH --mail-user=tr44022@uga.edu
#SBATCH --ntasks=1
#SBATCH --mem=10gb
#SBATCH --time=08:00:00
#SBATCH --output=MAFFT.%j.out
#SBATCH --error=MAFFT.%j.err

cd $SLURM_SUBMIT_DIR

# Load the correct MAFFT module
module load MAFFT/7.505-GCC-12.2.0-with-extensions

# Run MAFFT with --anysymbol option
mafft --anysymbol --auto USdata.fasta > aligned_USdata.fasta
```

# Realign 
```auspiceMainDisplayMarkdown
#!/bin/bash
#SBATCH --job-name=j_MAFFT
#SBATCH --partition=batch
#SBATCH --mail-type=ALL
#SBATCH --mail-user=tr44022@uga.edu
#SBATCH --ntasks=1
#SBATCH --mem=10gb
#SBATCH --time=08:00:00
#SBATCH --output=MAFFT.%j.out
#SBATCH --error=MAFFT.%j.err

cd $SLURM_SUBMIT_DIR

# Load the correct MAFFT module
module load MAFFT/7.505-GCC-12.2.0-with-extensions

# Run MAFFT with --anysymbol option
mafft --reorder aligned_USdata.fasta > realigned_USdata.fasta
```
