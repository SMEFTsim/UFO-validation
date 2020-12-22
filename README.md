# UFO-validation

`SMEFTsim` contains a set of UFO models that have been validated following the recommendations in [CERN-LPCC-2019-02](http://cds.cern.ch/record/2680993) and using the dedicated `MadGraph5_aMC@NLO` [plugin](code.launchpad.net/~rwgtdim6/mg5amcnlo/plugin_eft_contrib).

The procedure consists in pairwise comparisons between models, based on the values returned for a set of squared amplitudes. 

Given a list of 2-->n processes and a list of points in parameter space, the plugin computes the SM squared amplitude, the pure SM-L6 interference and the quadratic L6 contribution at one random phase-space point for each process and parameter point. The validation is considered successful if all the squared amplitudes agree within a permille.

The validation of the `SMEFTsim` UFOs was performed
- internally, comparing models with same flavor assumptions and different input scheme and viceversa.
- externally, comparing the `general`, `top` and `topU3l` models with m_W input scheme to [`dim6top`](feynrules.irmp.ucl.ac.be/wiki/dim6top) and [`SMEFT@NLO`](feynrules.irmp.ucl.ac.be/wiki/SMEFTatNLO)


This repository contains two types of files that have been produced in the validation process:
#### Parameter Cards

Each directory `cards_MODEL1_to_MODEL2` contains files named `param_XX.dat`, where `XX` is the name of a parameter in `MODEL2`.

This is a parameter card of `MODEL1` that corresponds to setting `XX = 1` and all other `MODEL2` parameters to 0.

These cards were used as input to the validation, and are provided here to aid the translation between different UFO models.

The models are labeled as follows:
- `general`: `SMEFTsim_general_MwScheme_UFO_v3_0`
- `utf`: `SMEFTsim_U35_MwScheme_UFO_v3_0`
- `MFV`: `SMEFTsim_MFV_MwScheme_UFO_v3_0`
- `top`: `SMEFTsim_top_MwScheme_UFO_v3_0`
- `topU3l`: `SMEFTsim_topU3l_MwScheme_UFO_v3_0`

Labels with an extra `A` indicate that the `alphaScheme` is used instead, for instance `generalA` refers to `SMEFTsim_general_alphaScheme_UFO_v3_0`.

The label `SMEFTatNLO` corresponds to the `SMEFTatNLO_U2_2_U3_3_cG_4F_LO_UFO` model released in 2018, while `SMEFTatNLOv1` denotes `SMEFTatNLO_v1_0` released in 2020.


#### PDF output files

The `output_PDFs` directory contains the PDF files produced as output by the validation plugin.

One file is produced for each comparison.

Discrepancies larger than a permille are marked in red, unless the absolute value of the squared amplitude is smaller than 1e-16 for both models, in which case they are blue.



