#!/bin/bash
#SBATCH -J SimpleMatcher
#SBATCH -p general
#SBATCH -o python%j.txt
#SBATCH -e python_%j.err
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --cpus-per-task=1
#SBATCH --time=168:00:00 
#SBATCH --mail-user=gklinge@iu.edu
#SBATCH --mail-type=BEGIN,END
#SBATCH --mem 100G
#SBATCH -A r00638
#SBATCH --array=1

module load python

python -m venv ~/myenv
source ~/myenv/bin/activate

pip install fuzzywuzzy matplotlib

Uncleaned_Unique_assignees="/N/u/gklinge/Quartz/Sorted/Sorted_unique_assignee/Unique_Assignee_sorted_by_Uncleaned.csv"
Cleaned_Unique_assignees="/N/u/gklinge/Quartz/Sorted/Sorted_unique_assignee/Unique_Assignee_sorted_by_Cleaned.csv"
UncleanedMatch="/N/u/gklinge/Quartz/Sorted/Sorted_crsp_permo/CSRP_Permco_Sorted_by_UnCleaned.csv"
CleanedMatch="/N/u/gklinge/Quartz/Sorted/Sorted_crsp_permo/CSRP_Permco_Sorted_by_Cleaned.csv"
output_csv="/N/u/gklinge/Quartz/Output/TestMatcher_December.csv"
unmatched_csv="/N/u/gklinge/Quartz/Output/unmatched_data_December.csv"
uncleaned_assignee_col="assignee"
cleaned_assignee_col="assignee_cleaned"
uncleaned_name_match_col="company_name"
cleaned_name_match_col="Cleaned_company_name"

cd $SLURM_SUBMIT_DIR

srun python YourMatchingScript.py "$Uncleaned_Unique_assignees" "$Cleaned_Unique_assignees" "$UncleanedMatch" "$CleanedMatch" "$output_csv" "$unmatched_csv" "$uncleaned_assignee_col" "$cleaned_assignee_col" "$uncleaned_name_match_col" "$cleaned_name_match_col"
