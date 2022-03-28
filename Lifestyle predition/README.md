**Bacteriophage lifestyle prediction based on HMM profiles**

1. **Clustering  of viral genomes based on ANI (Average Nucleotide Identity) and AF (Alignment Fraction)**

        perl Cluster_genomes_5.1.pl -f sample_viral.fna -d mummer-4.0.0rc1 -c 85 -i 95

2. **Compute protein-coding gene prediction**

        prodigal -i my.metagenome.fna -o my.genes -a my.proteins.faa -p meta

3. **All ORFs of each OTU were annotated using a custom set of 29 HMM profiles as described in manuscript**
        
        The 29 Pfam profile (PF07508, PF00589, PF01609, PF03184, PF02914, PF01797, PF04986, PF00665, PF07825, PF00239, PF13009, PF16795, PF01526, PF03400, PF01610, PF03050, PF04693, PF07592, PF12762, PF13359, PF13586, PF13610, PF13612, PF13701, PF13737, PF13751, PF13808, PF13843 and PF13358) was downloaded from 'http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz' of version 34.0 release (19-Mar-2021).

        hmmscan --cut_ga --tblout sample_protein.txt Pfam-A.hmm my.proteins.faa
