# Tree Time Code

```auspiceMainDisplayMarkdown
#!/bin/bash
#SBATCH --job-name=TreeTime
#SBATCH --partition=bahl_p
#SBATCH --ntasks=1
#SBATCH --ntasks-per-node=2
#SBATCH --cpus-per-task=8  
#SBATCH --mem=2G
#SBATCH --time=7-00:00:00
#SBATCH --output=log.%j.out
#SBATCH --error=log.%j.err
#SBATCH --mail-user=tr44022@uga.edu  
#SBATCH --mail-type=END,FAIL

# Change to the directory where the job was submitted
cd $SLURM_SUBMIT_DIR

ml load Python/3.10.4-GCCcore-11.3.0

# Create a virtual environment
python -m venv treetime_env

# Activate the virtual environment
source treetime_env/bin/activate

# Install TreeTime
pip install phylo-treetime

# Create output directory
output_dir="output"
mkdir -p $output_dir

treetime --sequence-length 1712 --tree realigned_USdata.fasta.nwk --dates USdata.csv --clock-filter 3.0 --reroot least-squares --outdir $output_dir

# Deactivate the virtual environment
deactivate
```
