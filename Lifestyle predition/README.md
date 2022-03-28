**Bacteriophage lifestyle prediction based on HMM profiles**

1. **Clustering  of viral genomes based on ANI (Average Nucleotide Identity) and AF (Alignment Fraction)**

        perl Cluster_genomes_5.1.pl -f sample_viral.fna -d mummer-4.0.0rc1 -c 85 -i 95

2. **Compute protein-coding gene prediction**

        prodigal -i my.metagenome.fna -o my.genes -a my.proteins.faa -p meta

        Pfam data was downloaded from 'http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz' of release (19-Mar-2021)

3. **All ORFs of each OTU were annotated using a custom set of 29 HMM profiles as described in manuscript**

        hmmscan --cut_ga --tblout sample_protein.txt Pfam-A.hmm my.proteins.faa
