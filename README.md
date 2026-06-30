# Toward Data-Driven Satellite Orbit Prediction: A Dataset and Method Survey for Multi-Regime Satellites

This repository provides the TLE dataset used in our paper. Observation and Precise Ephemeris data are available via the links below and can be downloaded separately.

---

## Directory Structure

```
dataset/
├── TLE/                        
│   ├── TERRA.tle
│   ├── QuakeSat.tle
│   ├── Pegasus.tle
│   ├── Haiyang-2A.tle
│   ├── Envisat.tle
│   ├── ERS-2.tle
│   ├── Technosat.tle
│   ├── Iridium-7.tle
│   ├── Iridium-118.tle
│   ├── NOAA-15.tle
│   ├── NOAA-16.tle
│   ├── BeiDou-2.tle
│   ├── Cryosat-2.tle
│   ├── TerraSAR-X.tle
│   ├── TanDEM-X.tle
│   ├── Jason-3.tle
│   ├── PAZ.tle
│   ├── Sentinel-6A.tle
│   ├── LAGEOS-1.tle
│   ├── LAGEOS-2.tle
│   ├── Larets.tle
│   ├── Stella.tle
│   ├── Blits.tle
│   ├── Starlette.tle
│   ├── Lares.tle
│   ├── Ajisai.tle
│   ├── Beacon-C.tle
│   ├── Etalon-1.tle
│   ├── Etalon-2.tle
│   ├── Swarm-A.tle
│   ├── Swarm-B.tle
│   ├── Swarm-C.tle
│   ├── GRACE-C.tle
│   ├── GRACE-D.tle
│   ├── GRACE-FO-C.tle
│   ├── GRACE-FO-D.tle
│   ├── Sentinel-3A.tle
│   ├── Sentinel-3B.tle
│   ├── Galileo-101.tle
│   ├── Galileo-203.tle
│   ├── Galileo-206.tle
│   ├── Elsa-D-CHS.tle
│   ├── Elsa-D-T.tle
│   ├── Elsa-D-TGT.tle
│   ├── Starlink-1008.tle
│   ├── Starlink-1270.tle
│   ├── Starlink-30506.tle
│   ├── GLONASS/
│   │   ├── GLONASS-041.tle
│   │   ├── GLONASS-095.tle
│   │   └── ... (43 satellites)
│   ├── Westford-Needles/
│   │   ├── westford_needles_602.tle
│   │   ├── westford_needles_628.tle
│   │   └── ... (multiple objects)
│   └── Intelsat/
│       ├── intelsat_1317.tle
│       ├── intelsat_2514.tle
│       └── ... (142 satellites)
└── 
```

---

## TLE Data

**Source:** [Space-Track.org](https://www.space-track.org)  
**Period:** 2004-01-01 ~ 2026-04-30  
**Format:** Two-Line Element (TLE), ordered by epoch ascending  

TLE files are provided directly in this repository. Each `.tle` file contains the full history of a satellite over the above period.

---

## Observation Data (SLR Full-Rate CRD)

Observation data consists of Satellite Laser Ranging (SLR) full-rate Consolidated Ranging Data (CRD) files. Download from the following sources:

**SLR CRD (CDDIS):**  
https://cddis.nasa.gov/archive/slr/data/fr_crd/

**GPS Observation:**  
https://www.earthdata.nasa.gov/data/space-geodesy-techniques/gnss/data-products-holdings

---

## Precise Ephemeris Data

Precise orbit ephemeris products must be downloaded from the following sources:

| Satellite | Source | Link |
|-----------|--------|------|
| Sentinel-3A/B, Sentinel-6A | Copernicus Data Space (CDSE) | https://documentation.dataspace.copernicus.eu/Data/SentinelMissions/Sentinel3.html#sentinel-3-precise-orbit-determination-pod-products |
| GRACE, GRACE-FO | NASA PO.DAAC | https://podaac.jpl.nasa.gov/cloud-datasets |
| Swarm-A/B/C | ESA Swarm DISC | https://swarm-diss.eo.esa.int/# |
| PAZ | ESA Earth Online | https://earth.esa.int/eogateway/catalog/paz-esa-archive |


## License

TLE data sourced from [Space-Track.org](https://www.space-track.org) is subject to Space-Track's terms of use. Users must agree to Space-Track's terms before accessing or redistributing TLE data.  
Observation and Precise Ephemeris data are subject to the terms of their respective providers (NASA, ESA, Copernicus).
=======
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
>>>>>>> 6713567e0908955afb4a51421358563ea8b2508a
