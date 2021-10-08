# Overview
Replicate the phylogenetic analyses in Henkel, Christiaan V., Erik Burgerhout, Daniëlle L. de Wijze, Ron P. Dirks, Yuki Minegishi, Hans J. Jansen, Herman P. Spaink, et al. “Primitive Duplicate Hox Clusters in the European Eel’s Genome.” PLOS ONE 7, no. 2 (February 24, 2012): e32231. https://doi.org/10.1371/journal.pone.0032231.

<img src="https://journals.plos.org/plosone/article/figure/image?size=large&id=info:doi/10.1371/journal.pone.0032231.g002" width="50%"> <img src="https://journals.plos.org/plosone/article/figure/image?size=large&id=10.1371/journal.pone.0032231.g003" width="40%">

# Analysis notes
## [09-28] Species tree
I'd like to obtain a species tree for the species used in the figure above. To do so, I copied the species names from Table S4 (in `data` folder) to a text file named `data/species-used-in-phylogeny.txt`. I found that the [timetree website](http://www.timetree.org/) capable of building a tree for selected species. The NCBI taxonomy browser has a [commmon tree](https://www.ncbi.nlm.nih.gov/Taxonomy/CommonTree/wwwcmt.cgi) tool that can perform the same function but often doesn't resolve the polytomy to a fine degree (perhaps it is more conservative and considers many of the branching uncertain).

## [10-08] Obtain sequences for alignment
### Other species homologs
1. The accession numbers for the sequences used in Figure 3 were transferred from Table S4 into a text file named `data/non-anguilla-accession-list-fig3.txt`.
1. Go to [batch entrez](https://www.ncbi.nlm.nih.gov/sites/batchentrez) website, choose "Protein" in the database dropdown menu and select the file we just created, click "Retrieve".
    - 42 sequences can be identified and retrieved. AY744145 turns out to be a nucleotide sequence. I replaced it with the ID of the corresponding protein entry AAW82627.
1. In the next page, locate the "send to" button on the top. Choose "File" -> "FASTA" and "Create file". Save the downloaded file and open it in any suitable editor (jEdit, Jalview, MEGA etc.)
### _A. anguilla_ sequences
Following the same protocol as above, except choosing "Nucleotide" in the database dropdown and in the "Send to" menu, choose "Coding sequences" and "FASTA Protein" in the format.

