# GeCoDiM (Gene Community Discovery Method)
## 1. EWGCD (Edge-Weighted Gene Community Detection)
### Overview
The **Edge-Weighted Gene Community Detection (EWGCD)** method identifies gene communities based on the weights of edges in a gene interaction network. This method emphasizes connections between genes by considering the edge weights to prioritize stronger relationships during community formation.
### Input Files
- `canonical_drivers.txt`: Contains a list of canonical driver genes.
- `prostate.maf`: Mutation Annotation Format file used to calculate mutation weights.
- `ReactomeFI_preprocessed_122718.txt`: Gene Network.
### Output Files
- `prostate.wmm`: Weighted mutation matrix for genes.
- `normalized_gene_scores.nwf`: Normalized gene scores.
- `ugn_gene_network.ugn`: Consensus gene network based on interaction frequencies.
- `gssn_gene_network.gssn`: Gene Strength Spreading Network.
- `community_results_largest_component.output`: Detected communities ranked by clustering coefficient and driver precision.
### Key Functions
- **calculate_clustering_coefficient**: Computes the clustering coefficient for a given community.
- **expand_cluster**: Expands a gene cluster starting from a seed node, based on edge weights.
- **detect_communities**: Identifies communities in the graph by iteratively expanding clusters.
- **rank_communities**: Ranks the detected communities based on clustering coefficient and driver precision.
- **save_communities_to_file**: Saves the detected and ranked communities to an output file.
### Heuristics
- **Principal Component Only**: In this method, only the largest (principal) connected component of the network is considered for community detection. This reduces noise from smaller, less relevant components and focuses the analysis on the most significant part of the network.
### Usage
Run the algorithm in the **/EWGCD** directory to identify gene communities based on the edge weights in the gene interaction network. The results will be saved in the output directory.

---
## NRGC (Normalized Random Gene Clustering)
### Overview
The **Normalized Random Gene Clustering (NRGC)** method discovers gene communities by random exploration and normalization of edge weights in a gene interaction network. This method provides an alternative approach where community detection is driven by probabilistic selection of edges.
### Input Files
- `canonical_drivers.txt`: Contains a list of canonical driver genes.
- `prostate.maf`: Mutation Annotation Format file used to calculate mutation weights.
- `ReactomeFI_preprocessed_122718.txt`: Gene Network.
### Output Files
- `prostate.wmm`: Weighted mutation matrix for genes.
- `normalized_gene_scores.nwf`: Normalized gene scores.
- `ugn_gene_network.ugn`: Consensus gene network based on interaction frequencies.
- `gssn_gene_network.gssn`: Gene Strength Spreading Network.
- `random_community_results_largest_component.output`: Detected communities ranked by clustering coefficient and driver precision.
### Key Functions
- **expand_randomly_with_weight**: Expands a gene cluster starting from a seed node, using normalized edge weights to determine the probability of including neighboring genes.
- **detect_communities_random**: Identifies communities in the graph by randomly expanding clusters.
- **rank_communities_with_precision**: Ranks the detected communities based on clustering coefficient and driver precision, with thresholds for minimum coefficient and precision.
- **save_communities_to_file**: Saves the detected and ranked communities to an output file.
### Heuristics
- **Principal Component Only**: Similar to the EWGCD method, only the largest (principal) connected component of the network is used for community detection. This ensures that the analysis is concentrated on the most significant network region.
- **Thresholding on Clustering Coefficient and Precision**: Communities are only saved if they have both a clustering coefficient and a precision score greater than 0.20. This heuristic filters out less significant communities, improving computational efficiency and focusing on higher-quality results.
### Usage
Run the algorithm in the **/NRGC** directory to identify gene communities using a random exploration approach. The results will be saved in the output directory.

---
## Sample Directory
The **/sample** directory is intended to showcase the functionality of the algorithms with a smaller dataset. It contains input files (`canonical_drivers_test.txt`, `maf_file.maf`, `GeneNetwork_1_large.txt`, `GeneNetwork_2_large.txt`, `GeneNetwork_3_large.txt`) in the **/inputs** folder and the corresponding output files (`test.wmm`, `normalized_gene_scores.nwf`, `ugn_gene_network.ugn`, `gssn_gene_network.gssn`, `community_results_2.output`, `community_results_4.output`) in the **/test** folder. This setup helps in understanding the workflow and results on a more manageable scale.

## License
MIT