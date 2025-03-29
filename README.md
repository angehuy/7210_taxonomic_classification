# 7210_taxonomic_classification
Conducting taxonomic classification including genus and species level classification, genotyping, and intra-contig analysis on assemblies
# Genotyping and Taxonomic and Quality Assessments: Group A3
**Group members:** Kevin Saju, Kristin Keith, Marissa Howard, Angela Huynh, Vedika Agarwal

Our pipeline performs genotyping, taxonomic classification, and quality assessments for genomic data. It integrates multiple tools to classify sequences at the genus level, species level, assess genome quality, and conduct intra-contig taxonomic evaluations.

## 📋 Pipeline Steps

1. **Genotyping**
   - Tool (1): MLST
     - Version: 2.23.0
   - Log(s):
     - ~/Pipeline_G3/logs/mlst_stderr.log
     - ~/Pipeline_G3/logs/mlst_stdout.log
   - Output(s):
     - ~/Pipeline_G3/output/mlst_results.tsv
       
2. **Genus Classification**
   - Tools (2): barnnap and RDP Classifier
     - Version:
        - barrnap: 0.9
        - RDP Classifier: 2.12
   - Log(s):
     - ~/Pipeline_G3/logs/16S_stderr.log
     - ~/Pipeline_G3/logs/16S_stdout.log
   - Output(s):
      - ~/Pipeline_G3/output/RDP_output.tsv
     
3. **Species Classification**
   - Tool (1): FastANI
     - Version: 1.34
   - Log(s):
     - ~/Pipeline_G3/logs/fastani.log
   - Output(s):
      - ~/Pipeline_G3/output/fastani_results/fastani_results.tsv

4. **Quality Control**
   - Tool (1): CheckM
     - Version: 1.2.3
   - Log(s):
     - ~/Pipeline_G3/logs/checkm.stderr.log
     - ~/Pipeline_G3/logs/checkm.stdout.log
   - Output(s):
      - ~/Pipeline_G3/output/checkm/checkm.tax.qa.tsv
     
5. **Intra-contig Taxonomic Assessment**
   - Tool (1): MMSeqs2
     - Version: 16.747c6
   - Log(s):
     - ~/Pipeline_G3/logs/top_mmseq_output.log
     - ~/Pipeline_G3/logs/top_mmseq_output_m8.log
   - Output(s):
      - ~/Pipeline_G3/output/mmseq/top_all_result.m8

### ⚙️ System Information
| Item | Specification |
|---|---|
| OS | macOS(ARM64) |
| Memory | 32 GB |
| Shell | zsh |
| Package Manager | Conda (Miniforge3) |

### ⚙️ Software Dependencies
* prodigal
* miniforge3
* Rosetta2
* Docker


### 🧬 Considerations for running the pipeline!
* To run this pipeline you will need to either download or clone the Pipeline_G3_final.tar.gz to your Downloads folder in your home directiory and expand the compressed file.
* Once the file has been expanded, you should have a "Pipeline_G3" folder. This folder contains the shell scripts you will need for the pipeline as well as an "asm" folder. Within this folder is a genome assembly from our sample set to test this pipeline. However, should you want to test more assemblies, you can access the link below and import more assemblies into the "asm" folder.
* This pipeline runs one bash script that executes our MLST, barrnap & RDP Classifier, FastANI, CheckM, and MMSeq2 analyses. Pipeline steps with their respective versions, outputs, and logs are detailed above.
* You need to have Docker open and running in the background of your computer for this pipeline to work.


### 📊 Data and Sample Information
* [Link to Assemblies](https://gtvault.sharepoint.com/:f:/s/TeamABIOL7210Spring2025/Erh9u1iPGNFFow3mSgCIbBsBLuvKnvCIKsVzFUNNHI97Yw?e=vSHnzm)
* | Sample | Filename |
   |---|---|
   | Smallest | A2128696filtered_assembly.fna |
   | Largest | A2128694filtered_assembly.fna |

## 🧬 Running the final pipeline
```
#This pipeline is compatible with a osx-64 platform on a Mac computer using zsh.
#Before running this script, open docker and have it running in the background of your computer.
#Ensure that you have downloaded the Pipeline_G3_final.tar.gz from this repository into your ~/Downloads directory on your Mac computer. This zip file contains 

#Make sure you are in your home directory
cd ~/

#Expand the compressed Pipeline_G3_final.tar.gz file - the expanded file should now be in your home directory
tar -xvzf ~/Downloads/Pipeline_G3_final.tar.gz

#Navigate into your Pipeline_G3 folder and give yourself permissions to run the scripts within it.
cd ~/Pipeline_G3
chmod 777 ./pipeline.sh ./mmseq_downloading_contigs.sh

#Run your pipeline shell
./pipeline.sh

```

