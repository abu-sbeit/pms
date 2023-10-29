# pms
Replication of Supervised Learning of Process Discovery Techniques using Graph Neural Networks

This repository contains the source code for the paper 'Process Discovery using Graph Neural Networks' [[1]](#1).


This project has several 'main' files with different purposes:
Run with --help to show the usage, i.e. which additional arguments should be used for each script.

E.g. `python3 -m project/ml_models --help`.   

### Training a new model
Example usage:
`python3 -m project.ml_models -d /Users/abdalrhman/Documents/process_trees_medium_ws2 
-md ./project/ml_models/models -mf example -fc`

### Process model discovery
`./project/process_mining/__main__.py`

Example usage:
`python3 -m project.process_mining -d /Users/abdalrhman/Documents/thesis_data/evaluation_data/BPI_2012_A/ -l data -m ai -tx 17 -bw -50 -bl 20 -np 20 -ln 0
         -mf ./project/ml_models/models/model_candidates_frequency_new_036.pth -cc
         -e repro`

### Compute and report conformance between process models and event logs
`python3 ./project/conformance/__main__.py`

### Analyzing properties of event logs
`./project/log_data_analysis/__main__.py`

### Generate event logs from Petri nets
`./project/data_generation/__main__.py`

Furthermore, the `evaluation` and `presentation` directories contain messy code used to generate respectively figures and animations.

### Remark
The code currently still contains hardcoded filepaths that link to a local filesystem.
The files that are used for training can be generated using ProM as mentioned in the paper.
The files that are used for evaluation are publicly available online as mentioned in the paper as well.
alternatively, these files are also hosted on https://gitlab.com/dominiquesommers/thesis_data and can be used accordingly.
Note that this does require the user to correct some hardcoded filepaths.

### Reproducing figure for evaluation results (Fig. x in [[1]](#1)).

Discover Petri nets using GNN (our method):

`python3 python3 scripts/evaluation_discovery_conformance_checking.py`

Discover models using other methods: prom/splitminer.

Conformance checking for other methods:

`python3 python3 scripts/evaluation_discovery_conformance_checking.py`

Generate plots:

`python3 scripts/evaluation_present_results.py -d /Users/abdalrhman/Documents/thesis_data/evaluation_data
-m fitness_entropy_partial precision_entropy_partial fitness_alignments precision_alignments -a gcn_medium_all split_reduced heuristics_reduced inductive_reduced -e`

`python3 scripts/evaluation_present_results.py -d /Users/abdalrhman/Documents/thesis_data/evaluation_data
-m fscore_entropy_partial fscore_alignments simplicity -a gcn_medium_all split_reduced heuristics_reduced inductive_reduced -e`


## References
<a id="1">[1]</a> 
Sommers, D., Menkovski, V., & Fahland, D. (2021, October). Process discovery using graph neural networks. In 2021 3rd International Conference on Process Mining (ICPM) (pp. 40-47). IEEE.
