# Advancing AI Research for Predicting Fluorescence Quantum Yields

## Overview

This proposal aims to advance artificial intelligence (AI) research by developing cutting-edge deep learning methods to predict fluorescence quantum yields (FQY) of molecules. FQY prediction is pivotal for designing efficient molecular probes and diagnostic tools in biomedical sciences. Accurate prediction of these yields will revolutionize medical imaging and diagnostic applications by enabling the design of more effective and reliable fluorescent molecules. 

Current machine learning and deep learning methods face significant limitations due to insufficient training data and inconsistent prediction accuracy. To overcome these challenges, this project will compile comprehensive datasets, integrate domain-specific knowledge, and leverage pretrained models with transfer learning techniques. These advancements will enable robust prediction of FQY for novel molecules. The project will culminate in the creation of a
publicly available dataset, high-performance predictive models, publications, and presentations. This initiative aligns seamlessly with NJIT’s mission to drive innovation in AI while promoting student development and engagement.

<img width="1028" height="365" alt="image" src="https://github.com/user-attachments/assets/4872f74b-ce71-4b0f-9801-1ddb1331f08b" />

# Current Approach/Progress

To predict the fluorescent quantum yield (FQY) from a given pair of molecule and solvent, we devised a model pipeline that first embedded both inputs into vectors, which were subsequently fed to downstream models for regression. To process the molecule and solvents, we first obtained the SMILES strings for each molecule and solvent, following which we fed both into the COATI model’s encoder to compute vector embeddings. COATI (Contrastive Optimization for Accelerated Therapeutic Inference) is a pre-trained, multimodal encoder-decoder model of druglike chemical space, which was primarily created to help with novel drug discovery. We adapt the models’ Grande encoder to fit our purposes by supplying SMILES strings to it and obtaining the vector embeddings for all 16k molecules and solvents.

Once the embeddings are computed, we also incorporated other input features alongside them as supplementary information, specifically, 310 RDKit-derived molecular properties, also obtained through the same SMILE strings, as well as the Morgan Fingerprints for each molecule. Results for varying input sizes and whether supplementary information is also attached are shown in Table I. Once all input features are calculated, we concatenate them to form a single vector
representation of the input which could be fed into 4 of our chosen downstream regression models:

1) MLP Regressor
2) XGBoost
3) LightGBM
4) Extra Trees Regressor

We are currently in the benchmarking and evaluation phase of the project, comparing multiple model approaches and baselines. Our focus at this stage is to validate performance across methods and ensure that all reported results are accurate, reproducible, and robust before inclusion in the final paper/publication. 

<img width="598" height="213" alt="image" src="https://github.com/user-attachments/assets/87c1f662-42a2-4fa4-ab75-3f24a6524ce0" />

## Citations

[COATI: multi-modal contrastive pre-training for representing and traversing chemical space](https://doi.org/10.26434/chemrxiv-2023-bdkgm).
