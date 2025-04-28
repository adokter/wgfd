```bash
├── KCYS / KRIW
│   ├── R                                       # bioRad ppi objects
│   ├── images                                  # PNG maps of week–hour VID
│   └── observed*                               # Geotiffs with rda
├── gis                                         # DEM + 3 × 3 km covariate grid
│   ├── srd_3km_mask_land.tif
│   └── uswtdb_v7_1_20240814.geojson
├── index.html                                  # interactive map
├── model                                       # XGBoost inputs, observed VID, model
│   ├── WY_model.bin
│   ├── vid_cell_week_hour.csv
│   └── wy_grid.csv
├── predicted                                   # statewide VID predictions 
│   ├── final_predictions_multilayer_cv_K200.tif
│   ├── week19_predicted_reds_k200.png
│   └── week37_predicted_reds_k200.png
└── threshold_boundaries                        # GeoJSON confidence masks
    ├── KCYS_threshold_boundaries.geojson
    └── KRIW_threshold_boundaries.geojson
```

### Bands*

| band | description |
|------|-------------|
| **VIR** | Vertically Integrated Reflectivity (cm² km⁻²) – range-corrected column-sum of η |
| **VID** | Vertically Integrated Density – estimated birds km⁻² |
| **R**   | Range-correction factor applied to VIR/VID |
| **overlap** | Bhattacharyya overlap (0–1) between beam profile and bird layer |
| **eta_sum / eta_sum_expected** | Observed vs. expected η at each pixel |
| **azimuth** | Pixel bearing from the radar (°) |
| **adjusted_VID** | VID after azimuth or site-specific corrections |
| **mask** | 1 = retain, 0/NA = exclude (confidence filter) |

*Threshold boundary* polygons (one per radar) define the spatial extent where data quality is considered reliable; they can be used to clip images and to create the `mask` band.

### Interactive visualization

[Link](http://wgfd.s3-website-us-east-1.amazonaws.com/)