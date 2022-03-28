**Identify the crAss-like phage in metagenomic sample**

**1. crAssphage database preparation: **

  (i)  crAssphage reference genome form NCBI (NC_024711.1)
  (ii) crAssphage reference proteome form NCBI (NC_024711.1)
  (ii) 249 crAssphage genome (Guerin et al.)
  (iv) 2684 crAssphage family (Yutin et al.)

  blastn/x -db database.fa -query sample_viral.fna -evalue 1E-05 -outfmt  "7 qseqid sseqid qlen slen qcovhsp evalue pident length qstart qend sstart send" -out   blast.output

  Output were filtered on the basis of e-value less than 1E-05, BLAST query alignment length 350bp, and a minimum contig length of 70kb (representing near-complete crAss-like phage contigs).

**2. Lifestyle Predition of crAss-like phage contigs**

  Identification of open reading frames (ORFs) for each crAss-like phage contigs

  prodigal -i my.metagenome.fna -o my.genes -a my.proteins.faa -p meta

  ORFs were compared to custom set of 29 HMM profiles 

  Pfam data was downloaded from 'http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz' of release (19-Mar-2021)

  hmmscan --cut_ga --tblout sample_protein.txt Pfam-A.hmm my.proteins.faa

  Contigs with an ORF, which obtained a hit with atleast five HMM profile (as mentioned in manuscript) were classified as temperate/lytic phage.

**3. Taxonomic identity of predicted crAss-like phages was done on the basis of average nucleotide identity (ANI)**

  java -jar OAU.jar -f1 contig_seq.fasta -f2 crAss-like_ref_genome.fasta -u usearch -o OrthoANIu.out

  ANI of each predicted crAss-like phages were calculated with each of the sixty-five previously identified crAss-like phages genomes classified as genus I to X (Lee et al., 2016). 
