# Clustering
In order to explore sub structure in a set of objects, I will employ unsupervised clustering. I will use CLANS tool (CLuster ANalysis of Sequences, https://toolkit.tuebingen.mpg.de/tools/clans).
In my case, I have a set of sequences to cluster however the method works equally well for clustering any set of objects for which you have a pair-wise similarity matrix.

# Step1: Generate pair-wise similarity measures
Will use all-against-all blast to do so.
```
blastn -query  input_seq.fa -subject input_seq.fa -outfmt 6  -out Seqs_all_agnst_all_blast.out
```

# Step2: Parse the blast ouput to CLANS input format
CLANS input file format is as follows:
Seq1_ID  Seq2_ID  Score
1 57 0.848989505267963
I define attraction score as -log10(E-value)
```
perl 1_make_CLANS_input_cluster_probes.pl
```

# Step3: Run CLANS
```
java -jar clans.jar -load Seqs_attractionvals.clans
```
