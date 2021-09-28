# Overview
Replicate the phylogenetic analyses in Henkel, Christiaan V., Erik Burgerhout, Daniëlle L. de Wijze, Ron P. Dirks, Yuki Minegishi, Hans J. Jansen, Herman P. Spaink, et al. “Primitive Duplicate Hox Clusters in the European Eel’s Genome.” PLOS ONE 7, no. 2 (February 24, 2012): e32231. https://doi.org/10.1371/journal.pone.0032231.

![The Hox gene clusters](https://journals.plos.org/plosone/article/figure/image?size=large&id=info:doi/10.1371/journal.pone.0032231.g002){:height="40%" width="40%}
![unrooted ML tree for Hox genes](https://journals.plos.org/plosone/article/figure/image?size=large&id=10.1371/journal.pone.0032231.g003){:height="40%" width="40%}

# Analysis notes
## [09-28] Species tree
I'd like to obtain a species tree for the species used in the figure above. To do so, I copied the species names from Table S4 (in `data` folder) to a text file named `data/species-used-in-phylogeny.txt`. I found that the [timetree website](http://www.timetree.org/) capable of building a tree for selected species. The NCBI taxonomy browser has a [commmon tree](https://www.ncbi.nlm.nih.gov/Taxonomy/CommonTree/wwwcmt.cgi) tool that can perform the same function but often doesn't resolve the polytomy to a fine degree (perhaps it is more conservative and considers many of the branching uncertain).
