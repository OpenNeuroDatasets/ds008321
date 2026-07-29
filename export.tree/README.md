# Spinal Cord Quantitative Susceptibility Mapping MRI dataset with total ΔB0, local ΔB0 and χ map

## Dataset description
This dataset includes total ΔB0 calculated from multi-echo gradient-recalled echo (meGRE) 3 T MRI, local ΔB0 maps processed with five background field removal algorithms (with 2 configurations: brain-recommended and spinal cord-optimized), and χ maps processed with five dipole inversion algorithms (with 2 configurations: brain-recommended and spinal cord-optimized). Eight participants were scanned using Siemens 3T scanners (MAGNETOM Prisma-Fit) equipped with head and neck coils. The data provided covers C1 to C5.

## Participants
- Total participants: 8
- Males: 6
- Females: 2
- Age: Mean = 23.0 years, SD = 2.2, range = 21-26 years
- Weight: Mean = 73 kg, SD = 8, range = 60-85 kg
- Height: Mean = 177.3 cm, SD = 7.7, range = 162-184 cm

## MRI Acquisition
- Scanner Model: Siemens MAGNETOM Prisma-Fit (3T)
- Coils used: Head and neck
- Structural images: T1-weighted MPRAGE
  - Resolution: 1 mm³
- QSM images: 5-echo multi-echo gradient-recalled echo
  - Resolution: 0.44 × 0.44 × 5 mm
  - FOV: C1 to C5

## Structural segmentation
Description of the _sct_ derivatives sub folder using the Spinal Cord Toolbox [1]: the magnitude (1st echo) of the meGRE were used to create the spinal cord, gray matter and white matter masks. The vertebrae-level segmentation was acquired in the T1w space and registered to the meGRE magnitude. 

## QSM processing 
- Total field maps (ΔB0) were generated using the ROMEO [2] through their command-line interface, each participants folder contains the total ΔB0 (in Hz) and the unwrapped phase.
- Local ΔB0 were calculated using 5 background field removal algorithms implemented in the SEPIA toolbox [3]: PDF, LBV, SHARP, RESHARP, and VSHARP. For each participant, there are 2 parameter configurations for each algorithm: brain-recommend (denoted by the _def_ prefix) and Spinal Cord optimized (denoted by the _opt_ prefix).
- χ maps were calculated using 5 dipole inversion algorithms implemented in the SEPIA toolbox: TKD, closed form, iLSQR, MEDI, and FANSI. For each participant, there are 2 parameter configurations for each algorithm: brain-recommend (denoted by the _def_ prefix) and Spinal Cord optimized (denoted by the _opt_ prefix). Additionally, for the iLSQR and closed form algorithms, there is a folder with the _auto_ prefix which used SEPIA's implementation of finding the regularization weight from an L-curve analysis.

## Dataset files and structure
This dataset is organized according to the BIDS format. Key directories and files include:
- /derivatives: Includes masks, segmentations, total ΔB0, local ΔB0 and χ maps
For ethics reasons, T1w and meGRE magnitude and phase are not publicly available. 

## References
[1] De Leener B, Lévy S, Dupont SM, et al. SCT: Spinal Cord Toolbox, an open-source software for processing spinal cord MRI data. Neuroimage. 2017;145(Pt A):24-43.
[2] Dymerska B, Eckstein K, Bachrata B, et al. Phase unwrapping with a rapid opensource minimum spanning tree algorithm (ROMEO). Magn Reson Med. 2021;85(4):2294-2308.
[3] Chan KS, Marques JP. SEPIA-Susceptibility mapping pipeline tool for phase images. Neuroimage. 2021;227(117611):117611.