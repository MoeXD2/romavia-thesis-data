# RomaVia Thesis Data

[![DOI](https://zenodo.org/badge/1252744877.svg)](https://doi.org/10.5281/zenodo.20435088)

This repository contains derived datasets and analytical outputs used in the thesis:

**RomaVia – A Data-Driven Approach to Mitigating Transit Uncertainty in Rome**

The thesis studies Rome’s surface public transport information reliability, with a focus on buses and trams. It examines the gap between physical transit operations and passenger-facing digital information, especially under conditions such as missing realtime data, stale predictions, ghost buses, feed desynchronization, route-variant ambiguity, and fallback dependency.

## Purpose of This Repository

This repository is provided to improve transparency and reproducibility of the thesis evidence base.

The files here support analysis of:

* passenger-reported surface transit complaints;
* social-media complaint classification;
* route-level complaint intensity;
* stop-level hotspot mapping;
* repeated stop-query interval proxies;
* GTFS-Realtime feed stability;
* certainty degradation in live predictions;
* VehiclePositions fallback dependency;
* spatial stop density and route characteristics.

These files are thesis-derived research artifacts. They are not official datasets from ATAC, Roma Capitale, Roma Mobilità, or any transport authority.

## Important Limitations

The datasets in this repository must be interpreted cautiously.

They do **not** provide:

* official service-performance measurements;
* representative passenger survey results;
* verified physical arrival records;
* city-wide punctuality statistics;
* proof that a specific route objectively failed;
* proof that RomaVia improves passenger trust or physical service reliability.

The social-media datasets are self-selected and non-representative. They reflect public complaint visibility, not the full passenger population.

The backend telemetry datasets measure information quality as observed by RomaVia. They do not automatically measure physical bus punctuality or actual service delivery.

The spatial files and route rankings are analytical outputs generated from the thesis methodology. They should not be treated as official service-failure maps.

## File Overview

### Social-Media Complaint Analysis

| File                            | Description                                                                                |
| ------------------------------- | ------------------------------------------------------------------------------------------ |
| `atac_tweet_analysis.json`      | Structured AI-assisted classification output for collected public transit complaint posts. |
| `atac_tweet_analysis_flat.csv`  | Flattened CSV version of the classified complaint dataset.                                 |
| `atac_tweet_analysis_log.txt`   | Processing log from the tweet classification workflow.                                     |
| `tweets_linked_with_quotes.csv` | Tweet dataset with linked or quoted context preserved where available.                     |
| `tweets_hotspot_candidates.csv` | Filtered complaint records considered usable for hotspot or spatial analysis.              |
| `tweet_analysis_summary.json`   | Summary statistics from the tweet classification process.                                  |

### Stop-Level Hotspot Outputs

| File                               | Description                                                    |
| ---------------------------------- | -------------------------------------------------------------- |
| `atac_surface_hotspots.geojson`    | GeoJSON output of mapped surface-transit complaint hotspots.   |
| `atac_surface_hotspots_mapped.csv` | CSV version of mapped hotspot records with spatial attributes. |

### Route-Level Complaint Analysis

| File                                     | Description                                                                                                      |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `route_complaint_summary.csv`            | Route-level summary of complaint counts, information failures, physical failures, severity, and weighted scores. |
| `top_routes_by_complaints.csv`           | Routes ranked by classified complaint count.                                                                     |
| `top_routes_by_information_failures.csv` | Routes ranked by information-failure complaint count or share.                                                   |
| `top_routes_by_weighted_score.csv`       | Routes ranked by the thesis heuristic weighted complaint score.                                                  |
| `route_intensity.geojson`                | GeoJSON route-corridor output showing complaint intensity by GTFS-derived route geometry.                        |
| `route_spatial_characteristics.csv`      | Spatial characteristics of complaint-linked routes or corridors.                                                 |

### Backend Telemetry and GTFS-Realtime Analysis

| File                          | Description                                                                                                              |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `feed_stability_analysis.csv` | Feed-age and stability analysis for GTFS-Realtime feeds observed by RomaVia.                                             |
| `certainty_analysis.csv`      | Classification of live prediction certainty states, including degraded prediction observations.                          |
| `vp_fallback_analysis.csv`    | VehiclePositions fallback dependency analysis, showing where vehicle-position evidence supported information continuity. |

### Stop-Query and Spatial Structure Analysis

| File                       | Description                                                                            |
| -------------------------- | -------------------------------------------------------------------------------------- |
| `stop_wait_times.json`     | Repeated stop-query interval proxy dataset used to study application polling behavior. |
| `spatial_stop_density.csv` | Spatial stop-density analysis derived from GTFS stop locations.                        |

## Methodological Notes

### Social-Media Complaint Data

The social-media analysis uses public complaint posts related to Rome public transport. The classification workflow separates:

* physical service failures, such as delay, overcrowding, breakdown, no-show, and suspension;
* informational failures, such as ghost buses, wrong ETAs, missing realtime data, disappearing vehicles, stale predictions, and app/feed mismatches.

The classification was AI-assisted and filtered by relevance, mode, confidence, and surface-transport focus. Metro-only and rail-only records were excluded from the final surface-transit analysis.

These data should be interpreted as passenger-reported perception evidence, not as official operational truth.

### Backend Telemetry Data

The telemetry files were generated from RomaVia backend observations of GTFS-Realtime behavior. They focus on information quality, including:

* TripUpdates and VehiclePositions feed age;
* feed desynchronization;
* certainty degradation of live predictions;
* fallback dependence on VehiclePositions;
* route-stop-level instability patterns.

These outputs help show that informational uncertainty can be observed and classified inside a backend mitigation layer. They do not prove physical vehicle delay or service failure.

### Route and Spatial Outputs

The GeoJSON and route-level files were generated by linking classified complaint records and backend-derived metrics to GTFS route, stop, and shape data. Route geometries should be interpreted as scheduled GTFS corridors, not necessarily the exact path of a specific vehicle at the time of a complaint.

## Repository Status

This repository supports a thesis proof-of-concept. The datasets may be updated, reorganized, or expanded if additional telemetry, validation data, or documentation becomes available.

## License and Use

This repository is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

You may share, copy, redistribute, adapt, transform, and build upon the material for any purpose, including commercial use, provided that appropriate attribution is given.

Recommended attribution:

Hndauoi, M. K. (2026). *RomaVia thesis data: Derived datasets for analysis of transit information uncertainty in Rome*. GitHub. https://github.com/MoeXD2/romavia-thesis-data