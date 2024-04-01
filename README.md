# CWRU Bearing Dataset in .npz format

The present repository presents the CWRU Bearing dataset in .npz format, corrected and reduced as far as some metadata are concerned. All credits for the dataset belong to CWRU.

## Dataset Overview

The CWRU Bearing dataset is an open-source dataset provided [here](https://engineering.case.edu/bearingdatacenter) by the Case School of Engineering of the Case Western Reserve University. The data correspond to time-series measured at locations near to and remote from motor bearings of a 2 HP Reliance Electric motor. As far as the experimental procedure is concerned, the CWRU webpage states:

> Motor bearings were seeded with faults using electro-discharge machining (EDM). Faults ranging from 0.007 inches in diameter to 0.040 inches in diameter were introduced separately at the inner raceway, rolling element (i.e. ball) and outer raceway. Faulted bearings were reinstalled into the test motor and vibration data was recorded for motor loads of 0 to 3 horsepower (motor speeds of 1797 to 1720 RPM).

A more detailed presentation of the methodology can be found [here](https://engineering.case.edu/bearingdatacenter/apparatus-and-procedures).

## Motivation

The present repository was created for two main reasons:

1. The original dataset is given in .mat format, as MATLAB was (and still is, to some extent) the mainstream tool for data analysis in Engineering problems. Nonetheless, with the advances that Deep Learning has seen in the past decade, this dataset is being widely used to train, evaluate and deploy DL models. The mainstream frameworks for such tasks are written in Python, so converting the files directly to .npz format allows DL researchers and enthusiasts to easily and quickly load and subsequently convert them to tensor objects and feed them to NNs or other models.

2. The original files contain some inconsistencies and (perhaps) redundancies when it comes to their metadata (see [Changes](#changes) for more information). The version presented here contains only the time-series data necessary for analysis and DL.

## Data Files

The original data files are in .mat format and are split into four different "families", depending on the motor's load and by extension its speed in RPM: 1797 (Load: 0 HP), 1772 (Load: 1 HP), 1750 (Load: 2 HP) and 1730 (Load: 3 HP). For each RPM value, the data are split in three main categories: Normal Baseline Data, containing time-series for normal bearings, Drive End (DE) Bearing Fault Data, containing time-series for bearings with single-point drive end defects and Fan-End (FE) Bearing Fault Data, containing time-series for bearings with fan end defects. For the DE case, data have been collected with two different frequencies, namely 12 kHz and 48 kHz, while FE data were collected at 12k samples/second.



Each .mat file may contain one or more time-series related to accelerometer data. The time-series can correspond to DE accelerometer data, FE accelerometer data or base (BA) accelerometer data. Additionally, each .mat file has a unique identifier which can be found as the last key of the .mat files' metadata. Its format is `X___`, where `___` is a 3-digit code. For our purposes, we will use the `RPM_Fault_Diameter_End` format to identify each files, where:

* `RPM` identifies the family in terms of RPM
* `Fault` identifies the anomaly type of the file's time-series (can be `IR`, `B`, `OR@6`, `OR@3` or `OR@12`)
* `Diameter` identifies the fault's diameter in milli-inches (can be `7`, `14`, `21` or `28`)
* `End` identifies the location and can be either `FE` or `DE12` / `DE48`, depending on the sampling rate (12 kHz and 48 kHz, respectively)

However, the `X___` format is used in the [Changes](#changes) section to highlight the issues with the original .mat files.

## Changes

TODO

## Attribution

All credits for the dataset belong to CWRU. This corrected and reduced version of the dataset was developed for the purposes of the following publication:

```
TODO
```

Nonetheless, citing this paper is not required for researchers who used this version of the dataset.
