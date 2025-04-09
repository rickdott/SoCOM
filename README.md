Sequence of Cognitive Operations - Model
==========

Repository used for the paper (IN SUBMISSION): *Sequence models for by-trial decoding of cognitive strategies from neural data*

Following research on cognitive processing stages and localizing their onset:
- Borst, Jelmer P., and John R. Anderson. “The Discovery of Processing Stages: Analyzing EEG Data with Hidden Semi-Markov Models.” NeuroImage 108 (March 2015): 60–73. https://doi.org/10.1016/j.neuroimage.2014.12.029.

- Anderson, John R., Qiong Zhang, Jelmer P. Borst, and Matthew M. Walsh. “The Discovery of Processing Stages: Extension of Sternberg’s Method.” Psychological Review 123, no. 5 (October 2016): 481–509. https://doi.org/10.1037/rev0000030.

- Weindel, Gabriel, Leendert van Maanen, and Jelmer P. Borst. “Trial-by-Trial Detection of Cognitive Events in Neural Time-Series.” Imaging Neuroscience 2 (December 16, 2024): 1–28. https://doi.org/10.1162/imag_a_00400.

## Instructions
The code for this project consists of three repositories:
- [The one you are currently viewing](https://github.com/rickdott/SoCOM/), containing notebooks that interact with the other two repositories.
- [A forked version of HMP](https://github.com/rickdott/hmp/tree/v1.0.0).
- [A Python package (HMP-AI)](https://github.com/rickdott/hmp-ai/tree/v1.0.0), created to make working with HMP and S4/ML models easier.

I used a Docker image on a remote server to run the code, Docker scripts and miscellaneous install scripts (some specific to UU server architecture) can be found in the `/docker` folder. `/docker/requirements.txt` can be used as a guide to install Python packages needed by the code.

Install the linked versions of HMP and HMP-AI by executing `pip install -e .` from their respective directories.

The `/weindel` and `/boehm` contain the analysis notebooks for their respective datasets. Everything can be executed in order, but heed instructions in the individual notebooks. Raw files should be available at a location that corresponds to an environment variable: `$DATA_PATH`, `$DATA_PATH/sat2` for Weindel, and `$DATA_PATH/sat1` for Boehm.

## Contact the author
r.denotter@uu.nl\
rickdotyt@gmail.com