**Bacteriophage lifestyle prediction based on HMM profiles**

**Compute protein-coding gene prediction**

prodigal -i my.metagenome.fna -o my.genes -a my.proteins.faa -p meta

Pfam data was downloaded from 'http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz' of release (19-Mar-2021)

**All ORFs of each OTU were annotated using a custom set of 29 HMM profiles as described in manuscript**

hmmscan --cut_ga --tblout sample_protein.txt Pfam-A.hmm my.proteins.faa
