# OzoneSensitivity

## Literature survey

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


## Dataset

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