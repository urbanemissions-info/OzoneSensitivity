# OzoneSensitivity

## Table of Contents
1. [Literature Survey](#literaturesurvey)
2. [Dataset](#dataset)
3. [Method](#method)

## Literature survey <a name="literaturesurvey"></a>

#### Examining TROPOMI formaldehyde to nitrogen dioxide ratios in the Lake Michigan region: implications for ozone exceedances

1. Compared O3 sensitivity on weekdays and weekends. NO2 sensitive on weekends.
2. Compared O3 sensitivity on O3 season days and O3 exceedance days.
3. HCHO and NO2 have similar lifetimes in order of hours
4. O3 season is defined as the time period in which most number of O3 exceedance days are present. O3 exceedance day is defined as a day on which atleast one ground monitor reports an MDA O3 level > NAAQS standard (70ppbv)
5. O3 sensitivity through FNR is prone to errors. But these errors are less in Urban areas. 
6. Cloud fraction considered - <0.5
7. To compare the differences in means Kolmogorov-Smirnoff test (K-S) was used. Null Hypothesis: Two samples come from same population. 
8. 


| FNR threshold  |  O3 sensitivity |
|---|---|
| FNR < 3.2 | VOC-sensitive |
| 3.2 < FNR < 4.1 | Transition zone |
| FNR > 4.1 | NOx-sensitive |
(Jin et al,. (2020))

#### Mirrezaei - Ozone production over arid regions

1. They used OMI data as well, apart from TROPOMI
2. Aridity Index (AI) - to determine the level of aridity of a region. It is calculated by dividing Mean Annual precipitation by Mean Annual Reference Evapotranspiration (PET). Global Aridity Index has this data. 

| AI  |  Aridity |
|---|---|
| AI < 0.03 | Hyper-arid |
| 0.03 < AI < 0.2 | Arid |
| 0.2 < AI < 0.5 | Semi-Arid |
| 0.5 < AI < 0.65 | Dry sub-humid |
| 0.65 < AI | Humid |
| 0.65 > AI | Drylands |
As per UNEP

3. Delhi is a dryland
4. More aridity (and elevated temperatures) => More ozone concentration, through acceleration of photochemical reactions. But, Elevated humidity levels have potential to enhance clouds and act as a proxy for HOx -- whihc may result in the efficiency of photochemical reactions.
5. Issues with satellite based FNR Ratio: errors in satellite retrievals, lack of vertically resolved data, use of constant FNR thresholds on satellite retrievals may increase uncertainty.
6. Major issue: uncertain correlation between HCHO and surface level organic reactivity. (for it to act as proxy to VOCs)
7. Relative impact of meteorological conditions on ozone production is less in dry areas.
8. Paper investigated the change in ozone regime during COVID19 lockdown. 
9. Data Quality - No discussion on cloud cover. QA as used in GEE L3. 


## Dataset <a name="dataset"></a>

### Google Earth Engine L3 prooduct of S5P TROPOMI

The S5P satellite was launched in October 2017 and has a
polar, sun-synchronous orbit, providing global daily data approximately at 13:30 LST (local solar time) (Ludewig et al.,2020). TROPOMI is an ultraviolet–visible–near-infrared–
shortwave-infrared nadir-viewing grating spectrometer on
board the S5P satellite that measures trace gases in the atmosphere as well as cloud and aerosol properties (Veefkind
et al., 2012; van Geffen et al., 2020). The original spatial resolution of TROPOMI data was 3.5 km × 7 km. Since
August 2019, the spatial resolution has been upgraded to
3.5 km × 5.5 km (van Geffen et al., 2020). To calculate
satellite FNRs, we utilize level 3 (L3) TROPOMI NO2
and HCHO tropospheric vertical column density (VCD) retrievals for the O3 seasons of 2019-2023. L3 product is prepared by Google Earth Engine.

The conversion to L3 is done by the harpconvert tool using the bin_spatial operation. The source data is filtered to remove pixels with QA values less than:

- 80% for AER_AI
- 75% for the tropospheric_NO2_column_number_density band of NO2
- 50% for all other datasets except for O3 and SO2

#### Issues with this data
1. **HCHO**: -0.0172 mol/m^2

## Method  <a name="method"></a>

1. [FNR Script - GEE](https://code.earthengine.google.com/a388006ea7b1e9c83005c1d53d5afd9e): This script is used to download the FNR tif for each month and season for the city of Delhi. 50 Cloud fraction is used in consistence with literature. All these FNR tifs are placed in the folder `data\FNR`
2. `FNR plots.ipynb` in the `scripts` folder plots the FNR as a PNG by considering 2.2-3.7 as the transition zone.