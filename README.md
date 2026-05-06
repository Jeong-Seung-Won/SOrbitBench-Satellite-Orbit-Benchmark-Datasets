# SOrbitBench

Official repository for **“SOrbitBench: A Large-Scale Multi-Regime Benchmark and Evaluation Pipeline for Satellite Orbit Prediction.”**

This repository provides a sample subset of SOrbitBench, a large-scale satellite orbit benchmark dataset constructed from Two-Line Element (TLE) data across seven orbital regimes, propagated using high-fidelity propagators such as Orekit or SDP4.

The full benchmark dataset and evaluation pipeline are described in the paper. Due to distribution constraints, only a representative sample is publicly available in this repository.

Due to the large size of our dataset of 3.5TB, we are providing you with the sample dataset which provides insights of our full dataset. The sample dataset was constructed by randomly selecting 2 satellites per orbital regime (14 satellites in total across 7 regimes), with all available part files included for each selected satellite. when our paper gets accpeted we will publish the whole dataset in the dataverse webpage with restricted access provided only for research and education purposes.

## Directory Structure

```
src/
├── Original/               # Raw TLE data collected from Space-Track
│   ├── _metadata/              # NORAD ID lists and satellite name mappings
│   │   ├── leo_payload_norads.txt
│   │   ├── non_leo_payload_norads.txt
│   │   └── norad_to_name.json
│   ├── LEO/                    # Low Earth Orbit satellites
│   ├── MEO/                    # Medium Earth Orbit satellites
│   ├── NSO/                    # Navigation Satellite Orbit satellites
│   ├── GEO/                    # Geostationary Earth Orbit satellites
│   ├── IGO/                    # Inclined Geosynchronous Orbit satellites
│   ├── EGO/                    # Extended Geostationary Orbit satellites
│   └── HAO/                    # High Altitude Orbit satellites
│
├── Interpolated/   # Orekit-propagated GCRF trajectories (1-min interval)
│   ├── LEO/
│   ├── MEO/
│   ├── NSO/
│   ├── GEO/
│   ├── IGO/
│   ├── EGO/
│   └── HAO/
│
└── Cleaned/        # Mission orbit extracted trajectories
    ├── LEO/
    ├── MEO/
    ├── NSO/
    ├── GEO/
    ├── IGO/
    ├── EGO/
    └── HAO/
```

## Data Format

Each `.npy` file contains a `(N, 6)` float64 NumPy array with the following columns:

| Index | Variable | Unit |
|-------|----------|------|
| 0 | x | km |
| 1 | y | km |
| 2 | z | km |
| 3 | vx | km/s |
| 4 | vy | km/s |
| 5 | vz | km/s |

## Orbital Regimes

| Regime | Description | Altitude Range |
|--------|-------------|----------------|
| LEO | Low Earth Orbit | 160 – 2,000 km |
| MEO | Medium Earth Orbit | 2,000 – 35,786 km |
| NSO | Navigation Satellite Orbit | 18,000 – 25,000 km |
| GEO | Geostationary Earth Orbit | ~35,786 km |
| IGO | Inclined Geosynchronous Orbit | ~35,786 km, i > 1° |
| EGO | Extended Geostationary Orbit | > 35,786 km |
| HAO | High Altitude Orbit | > 35,786 km |
