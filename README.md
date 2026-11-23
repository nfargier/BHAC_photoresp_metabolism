# BHAC vs native photorespiration in *S. elongatus* PCC 7942

Flux balance analysis (FBA) comparing a carboxysome-free *S. elongatus* PCC 7942 strain (ΔCCM) with and
without the β-hydroxyaspartate cycle (BHAC). The BHAC is an alternative route for recycling the glyoxylate
produced by Rubisco oxygenation. The analysis tests whether relying on the BHAC instead of native
photorespiration changes growth.


## Folders

```
1_data/        metabolic model
2_notebooks/   analysis notebook ipynb
3_results/     csv results and figures
```

## Data


`1_data/iMS837.json`  Genome-scale model of *S. elongatus* PCC 7942 (Santos-Merino et al., 2023), unmodified 

The notebook starts from `iMS837.json` and builds both strains itself

## Notebook

`2_notebooks/FBA_dCCM_BHAC.ipynb` runs the whole analysis. Run all cells; it loops over both C:O ratios and
both model variants and writes the csv files and the figure.

What it does:

1. **Builds the models.** ΔCCM: carboxysome reactions removed, cytosolic Rubisco with a fixed
   carboxylation-to-oxygenation (C:O) ratio, cytosolic carbonic anhydrase, NAD(P) transhydrogenase blocked.
   ΔCCM + BHAC: the four BHAC reactions (BhcA–D) added on top.
2. **Runs FBA** for both strains, under non-limited conditions (CO2 uptake fixed at 10 mmol gDW-1 h-1) and
   under light limitation (photosystem charge separation capped at 1 mmol gDW-1 h-1), at C:O ratios of 3:1
   and 1:1, with and without an added PEP carboxykinase reaction.
3. **Plots SI Fig. 2**: CO2 fixed per photon of the ΔCCM + BHAC strain, in % of ΔCCM.


## Requirements

Python 3.10 with cobrapy, numpy, pandas, matplotlib and a solver (Gurobi or GLPK). Escher is only needed to
edit the maps, not to run the analysis.
