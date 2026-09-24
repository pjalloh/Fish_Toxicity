# Data for: A benchmark dataset for machine learning in ecotoxicology

### Abstract

The use of machine learning for predicting ecotoxicological outcomes is promising, but underutilized. The curation of data with informative features requires both expertise in machine learning as well as a strong biological and ecotoxicological background, which we consider a barrier of entry for this kind of research. Additionally, model performances can only be compared across studies when the same dataset, cleaning, and splittings were used. Therefore, we provide ADORE, an extensive and well-described dataset on acute aquatic toxicity in three relevant taxonomic groups (fish, crustaceans, and algae). The core dataset describes ecotoxicological experiments and is expanded with phylogenetic and species-specific data on the species as well as chemical properties and molecular representations. Apart from challenging other researchers to try and achieve the best model performances across the whole dataset, we propose specific relevant challenges on subsets of the data and include datasets and splittings corresponding to each of these challenge as well as in-depth characterization and discussion of train-test splitting approaches.

### Overview

The ADORE dataset was created as part of the SDSC project "MLTox: Enhancing Toxicological Testing through Machine Learning". This ERIC Open Data  contains the benchmark data as well as some intermediate and explanatory files. This data, including raw files and code, is also available as a [public code repository](https://renkulab.io/projects/mltox/adore).

The core of ADORE is from [ECOTOX](https://cfpub.epa.gov/ecotox/), filtered to only contain data on acute mortality of fish, crustaceans and algae. It was extended with taxonomic information from [Add my Pet](https://www.bio.vu.nl/thb/deb/deblab/add_my_pet/index.html) and [TimeTree](http://timetree.org/) and chemical information from [PubChem](https://pubchem.ncbi.nlm.nih.gov/) and other sources. Please refer to the [paper pre-print](https://doi.org/10.1101/2023.05.27.542160) and the script `01_preprocessing_rawdata.py` in the above mentioned repository for detailed information on dataset generation.

### Files and file structure

All data is stored in the subfolders (`processed`, `chemicals`, `taxonomy`). All files are provided as csv or tsv. 

Intermediate files as well as the final files, one for each prediction challenge, can be found in the folder `processed`. We include the intermediate files such that the user can follow the processing steps. They encompass the processed separate files from ECOTOX for species (`ecotox_species.csv`), tests (`ecotox_tests.csv`), results (`ecotox_results.csv`), as well as compiled chemical properties (`ecotox_properties.csv`) in the subfolder `processed/before_aggregation`. These files are then combined to get `ecotox_mortality_processed.csv` and then filtered to get `ecotox_mortality_filtered.csv`. 

For each challenge, we provide a data subset which starts with the name of the challenge, e.g., `a-F2F` and ends with `_mortality.csv`. These datasets contain all information needed for modeling and columns to uniquely identify and retrace each entry (see below).

Additionally, we provide separate files in the folder `chemicals`. The chemical ontology (`classyfire_output.csv`) and the functional use categories (`functional_uses_output.csv`) can be matched with the data in the challenges files using the InChIkey or the DTXSID, respectively. Three files are explaining the bits of the MACCS, PubChem and ToxPrint (`maccs_bits.tsv`, `pubchem_bits.csv` and `toxprint_bits.csv`). The file `tax_pdm_species` in the folder `taxonomy` contains phylogenetic distance information which can be used for modeling.


### Retraceability

For the sake of retraceability, we retain the ECOTOX test and result id for each entry, which allows users to check entries against ECOTOX. Please [open an issue](https://gitlab.renkulab.io/mltox/adore/-/issues) if you find an error.


### Citation

Schür et al. (2023), A benchmark dataset for machine learning in ecotoxicology, Nature Scientific Data


### Licence

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.