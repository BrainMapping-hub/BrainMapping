# BrainMapping: A Computational Framework for Bidirectional Cross-Species Functional Mapping

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Learning bidirectional functional correspondence between human and rat brains from resting-state fMRI.

## Overview

**BrainMapping** is a computational framework for learning bidirectional functional correspondence between **human** and **rat** brains from resting-state fMRI (rs-fMRI).

Rather than assuming that anatomical homology alone is sufficient to define cross-species equivalence, BrainMapping learns **region-of-interest (ROI) representations in a shared functional space** and infers **distributed correspondences** between species. This allows cross-species comparison at the level of intrinsic functional organization, even when direct anatomical matching is incomplete or biologically implausible.

The framework is motivated by a central challenge in translational neuroscience: rodent models provide powerful access to cellular and circuit mechanisms, yet these findings often do not transfer cleanly to large-scale human brain organization. BrainMapping aims to help bridge this gap by relating localized rodent findings to distributed human brain networks.

## Motivation

Establishing functional correspondence across species is difficult for several reasons:

- Similar anatomy does not necessarily imply similar large-scale function.
- Direct ROI-level cross-species correspondence labels are not available.
- Strict one-to-one matching is often biologically implausible across species with different cortical scales, acquisition conditions, and evolutionary histories.

A useful cross-species mapping should therefore do more than pair individual regions. It should preserve broader principles of intrinsic brain organization, including **network structure**, **macroscale gradients**, and **graph topology**.

## Framework

BrainMapping is a three-stage framework for bidirectional cross-species functional alignment.

### Stage 1: Cross-Species Representation Pretraining (CRP)

A **shared-weight Transformer encoder** processes both human and rat ROI time series and learns a common representational space from intrinsic activity patterns.

### Stage 2: Biology-Informed Representation Refinement (BIR)

The pretrained ROI representations are refined using:

- **Self-supervision**, through reconstruction of masked voxel information
- **Biologically informed regularization**, based on principles of functional segregation and integration

This stage improves feature quality while preserving meaningful within-network structure and interpretability.

### Stage 3: Bidirectional Graph Matching via Optimal Transport (BGM-OT)

A **Graph Convolutional Network (GCN)** enriches ROI features with network-topological context, and an **optimal transport solver** (Sinkhorn algorithm) estimates a bidirectional probabilistic assignment matrix between species.

Rather than enforcing hard one-to-one matches, BrainMapping supports **distributed many-to-many correspondence**, which is more compatible with cross-species functional organization.

## Key Contributions

- Learns cross-species functional correspondence directly from **rs-fMRI**
- Does **not rely on anatomical homology** as the primary basis for alignment
- Builds a **shared functional representation space** for human and rat ROIs
- Estimates **bidirectional** and **distributed** mappings between species
- Incorporates **biological constraints** to improve interpretability and robustness
- Evaluates correspondence through preservation of large-scale brain organization when ROI-level ground truth is unavailable

## Validation Strategy

Because direct ROI-level cross-species ground truth is not available, BrainMapping is evaluated through **orthogonal preservation tests** rather than a single label-matching benchmark.

We assess whether mapped data retain key properties of native brain organization, including:

- **Network-level functional connectivity**
- **Macroscale functional gradients**
- **Graph topology**
- **Stability across held-out subjects**

This validation strategy is designed to test whether the learned mappings are biologically meaningful rather than merely statistically convenient.

## Findings

BrainMapping recovers a subset of cross-species relationships supported by previous studies and also suggests candidate correspondences that may warrant further investigation.

## Interactive Exploration

We also provide an interactive web tool for exploring the inferred cross-species mappings.

## Repository Status

This repository accompanies the **BrainMapping** paper. Code, pretrained models, and detailed usage instructions will be released after publication.

## Planned Contents

- Data preprocessing pipeline
- Model training and inference code
- Cross-species alignment and evaluation scripts
- Pretrained checkpoints
- Interactive mapping demo

## Citation

Citation information will be added here upon publication.

## License

This project is released under the MIT License.
