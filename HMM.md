HMM for Protein Analysis
==

Part I
--
[TMHMM](http://www.cbs.dtu.dk/services/TMHMM/) is a [hidden Markov model](http://en.wikipedia.org/wiki/Hidden_Markov_model)-based tool for predicting transmembrane helices and topology. The goal here is to use the [TMHMM](http://www.cbs.dtu.dk/services/TMHMM/) server to make a prediction and compare the results with the annotation of [AQP1_HUMAN](http://www.uniprot.org/uniprot/P29972).

1. How many transmembrane segments can you predict?

2. Based on the prediction of [TMHMM](http://www.cbs.dtu.dk/services/TMHMM/), is [AQP1_HUMAN](http://www.uniprot.org/uniprot/P29972) transmembrane protein?

3. The structure of this protein is known [PDB 1H6I](http://www.rcsb.org/pdb/explore/explore.do?structureId=1h6i). How does the [TMHMM](http://www.cbs.dtu.dk/services/TMHMM/) prediction compare to the experimentally determined structure?

4. Does the functional description/annotation of [AQP1_HUMAN](http://www.uniprot.org/uniprot/P29972) agrees with the [TMHMM](http://www.cbs.dtu.dk/services/TMHMM/) prediction?

Part II
--
In this exercise, we will start with using [Pfam](http://pfam.sanger.ac.uk/search) to identify the protein family of the unknown protein below (It is actually known but we will assume that it is unknown). Then we will see the identified protein family from [Pfam](http://pfam.sanger.ac.uk/search) is a somehow generic family. Next we will use [HMMER](http://hmmer.janelia.org/) to build *our own* more specific HMM models for subfamilies of the general family.

1. Predict the protein family of the following sequence using [Pfam](http://pfam.sanger.ac.uk/search). To which family does it belong?
<pre>
>My_Sequence
MGLSDGEWQLVLNVWGKVEADIPGHGQEVLIRLFKGHPETLEKFDKFKHLKSEDEMKASEDLKKHGATVL
TALGGILKKKGHHEAEIKPLAQSHATKHKIPVKYLEFISECIIQVLQSKHPGDFGADAQGAMNKALELFR
KDMASNYKELGFQG
</pre>

2. Go to [NCBI BLAST](http://blast.ncbi.nlm.nih.gov/Blast.cgi) and search for homologous sequences in the **human genome**.

3. Identify two *different* family members

4. For each family member, perform BLAST search again **with no restriction on the species**. From the BLAST results, collect the same family member from different species (between five and ten sequences per family).
5. Build a multiple sequence alignment using [MAFFT](http://mafft.cbrc.jp/alignment/server/). Save (download) the alignment as in the FASTA format

6. Convert the output alignment from FASTA to Stockholm using [this online converter](http://sequenceconversion.bugaco.com/converter/biology/sequences/fasta_to_stockholm.php)

7. Login to the server, IP address: <code>10.7.28.9</code> using [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/), Chrome [Secure Shell](https://chrome.google.com/webstore/category/apps?hl=en), or [Cygwin](https://www.cygwin.com/) via
<br>
<code>ssh your_student_id@10.7.28.9</code>.
<br>
The <code>password</code> is the same as the <code>username</code>.

8. Build HMM model from the two alignments using <code>hmmbuild</code> from [HMMER](http://hmmer.janelia.org/):
<br>
Example: <code>hmmbuild --amino protein_family.hmm protein_family.sto</code>

9. Search the human and fly proteins for each model and see how many proteins belong to each family:
<br>
Example: <code>hmmsearch protein_family.hmm human.fas</code>
<br>
Example: <code>hmmsearch protein_family.hmm fly.fas</code>

10. Describe the search results.
