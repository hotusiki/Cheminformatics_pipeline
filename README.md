# Cheminformatics Pipeline

Reproducible Colab-based workflows for structure-based drug discovery, protein structure analysis, docking, and molecular dynamics.

## Overview

This repository contains two main notebooks that cover complementary stages of a computational drug discovery workflow:

- **Predocking_docking.ipynb** — target-to-structure resolution, pocket identification, consensus binding-site analysis, GNINA docking, redocking calibration, and batch docking.
- **md_simulation.ipynb** — AMBER/OpenMM-based molecular dynamics workflow for protein–ligand and protein–nucleic-acid systems, followed by trajectory analysis and MM/GBSA post-processing.

The pipeline was developed for structural bioinformatics tasks in oncology-related research and is suitable for systems involving protein structures, ligands, and nucleic-acid-containing complexes, including R-loop-related setups.

## Repository contents

### 1. `Predocking_docking.ipynb`
A docking workflow that includes:

- target resolution against reviewed UniProt entries;
- retrieval of experimental PDB structures;
- detection and preprocessing of reference ligands;
- receptor preparation;
- route selection between:
  - **reference-ligand docking**
  - **pocket-consensus docking**
- pocket prediction and repair using:
  - **P2Rank**
  - **DoGSite**
- consensus pocket comparison using **Jaccard similarity** and residue-vote tables;
- ligand preparation;
- **GNINA** docking;
- redocking calibration;
- batch docking with resume support;
- final aggregation of docking results into a compact report.

### 2. `md_simulation.ipynb`
A molecular dynamics workflow that supports:

- protein + small-molecule ligand systems;
- protein + nucleic-acid ligand systems;
- AMBER topology building with **LEaP**;
- ligand parameterization with **GAFF2**;
- protein preparation with **pdb4amber**;
- trajectory production in **OpenMM**;
- analysis with:
  - **RMSD**
  - **RMSF**
  - ligand RMSD
  - metal coordination sanity checks
- MM/GBSA post-processing via **MMPBSA.py**;
- publication-ready parsing of MM/GBSA output tables.

## Key features

- Colab-ready execution
- Google Drive integration
- Modular workflow structure
- Support for both protein–ligand and protein–nucleic-acid systems
- Consensus pocket analysis for cases where no reference ligand is available
- Batch processing and resume support
- Trajectory analysis and free-energy post-processing
- Designed for transparent, reproducible structure-based modeling

## Tools and libraries

### Docking notebook
- GNINA
- P2Rank
- DoGSite
- UniProt
- PDB / RCSB retrieval
- RDKit
- Biopython

### MD notebook
- AMBERTools
- OpenMM
- ParmEd
- MDTraj
- MDAnalysis
- PDBFixer
- cpptraj
- MMPBSA.py

## Typical workflow

### Docking
1. Resolve target identifiers.
2. Download experimental structures.
3. Detect whether a reference ligand is available.
4. Preprocess the receptor.
5. Build either a reference-ligand route or a pocket-consensus route.
6. Prepare ligands.
7. Run GNINA docking.
8. Calibrate with redocking.
9. Run batch production docking.
10. Aggregate and inspect results.

### Molecular dynamics
1. Prepare protein and ligand inputs.
2. Parameterize the ligand.
3. Prepare the protein.
4. Build the complex.
5. Generate AMBER topology.
6. Run minimization and equilibration.
7. Run production MD in chunks.
8. Analyze trajectory stability and flexibility.
9. Perform MM/GBSA analysis.
10. Export the final results table.

## Requirements

The notebooks are designed for **Google Colab** and rely on conda-based installation inside the Colab environment.

Recommended environment:
- Google Colab
- Google Drive
- Python 3.10+
- conda / mamba
- AMBERTools
- OpenMM
- RDKit
- MDAnalysis
- MDTraj

## Usage

Open the notebooks in Google Colab and run the cells in order.

### Docking workflow
Open:
`Predocking_docking.ipynb`

### Molecular dynamics workflow
Open:
`md_simulation.ipynb`

Both notebooks are organized as step-by-step pipelines with helper functions, setup cells, and analysis sections.

## Notes

- The docking workflow is designed to work even when a reference ligand is missing.
- The MD workflow supports both small molecules and nucleic-acid ligands.
- The notebooks are structured to keep intermediate files, logs, manifests, and analysis outputs in a clear project directory layout.
- The pipeline is intended for research and educational use in structural bioinformatics and computational drug discovery.

## Repository link

GitHub: https://github.com/hotusiki/Cheminformatics_pipeline

## Author

Mарат Юнусов
