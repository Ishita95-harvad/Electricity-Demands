# Electricity-Demands
This dataset compiles and harmonizes multiple open smart meter datasets.

**Curated by:** Ishita95-harvad

**License:** BSD 3-clause "New" or "Revised" licence

**Uses**
This smart meter dataset facilitates primarily electricity demand forecasting.

**Dataset Structure**
## The dataset contains three main files.

data/demand.parquet
data/metadata.parquet
data/weather.parquet
data/demand.parquet

**This file contains the electricity consumption values and has three columns.**

**unique_id:** a unique id of the meter

**timestamp:** the start timestamp of the recording period in local time

**y:** the electricity consumption in the current period in kWh

data/metadata.csv

**This file contains the available metadata for every meter. The file contains the folloging columns:**

**unique_id**: the unique id of the meter

**dataset:** the name of the original dataset

**building_id:** the id of the meter in the original dataset

**location_id**: a unique geohash for the location

**latitude:** approximate latitude of the meter

**longitude:** approximate longitude of the meter

**location:** name of the location

**timezone:** timezone where the meter is located

**freq:** pandas style frequency string of the meter data

**building_class**: class of the building: Residential/Commercial

**cluster_size:** the number of buildings under the meter

data/weather.parquet
**This file contains weather data for all locations. The columns are the following:**

**location_id**: The unique id for the location.

**timestamp**: The timestamp of the observation in local time.

**temperature_2m**: Air temperature at 2 meters above ground. (°C)

**relative_humidity_2m**: Relative humidity at 2 meters above ground. (%)

**dew_point_2m:** Dew point temperature at 2 meters above ground. (°C)

**apparent_temperature**: Apparent temperature is the perceived feels-like temperature combining wind chill factor, relative humidity and solar radiation. (°C)

**precipitation:** Total precipitation (rain, showers, snow) sum of the preceding hour. Data is stored with a 0.1 mm precision. If precipitation data is summed up to monthly sums, there might be small inconsistencies with the total precipitation amount. (mm)
**rain:** Only liquid precipitation of the preceding hour including local showers and rain from large scale systems. (mm)

**snowfall:** Snowfall amount of the preceding hour in centimeters. For the water equivalent in millimeter, divide by 7. E.g. 7 cm snow = 10 mm precipitation water equivalent. (cm)

**snow_depth:** Snow depth on the ground. Snow depth in ERA5-Land tends to be overestimated. As the spatial resolution for snow depth is limited, please use it with care. (m)

**weather_code**: Weather condition as a numeric code. Follow WMO weather interpretation codes.

See table below for details.
## Weather code is calculated from cloud cover analysis, precipitation and snowfall. As barely no information about atmospheric stability is available, estimation about thunderstorms is not possible. (WMO code)

**pressure_msl:** Atmospheric air pressure reduced to mean sea level. Typically pressure on mean sea level is used in meteorology. Surface pressure gets lower with increasing elevation. (hPa)

**surface_pressure:** Atmospheric pressure at surface (hPa)

**cloud_cover:** Total cloud cover as an area fraction. (%)

**cloud_cover_low:** Low level clouds and fog up to 2 km altitude. (%)

**cloud_cover_mid**: Mid level clouds from 2 to 6 km altitude. (%)

**cloud_cover_high**: High level clouds from 6 km altitude. (%)

**et0_fao_evapotranspiration:** ET₀ Reference Evapotranspiration of a well watered grass field. 

## Based on FAO-56 Penman-Monteith equations ET₀ is calculated from temperature, wind speed, humidity and solar radiation. Unlimited soil water is assumed. ET₀ is commonly used to estimate the required irrigation for plants. (mm)

**vapour_pressure_deficit:** Vapor Pressure Deificit (VPD) in kilopascal (kPa). For high VPD (>1.6), water transpiration of plants increases. For low VPD (<0.4), transpiration decreases. (kPa)

**wind_speed_10m**: Wind speed at 10 meters above ground. (km/h)

**wind_direction_10m:** Wind direction at 10 or 100 meters above ground. (°)

**wind_gusts_10m**: Gusts at 10 meters above ground of the indicated hour. Wind gusts in CERRA are defined as the maximum wind gusts of the preceding hour.

## Please consult the ECMWF IFS documentation for more information on how wind gusts are parameterized in weather models. (km/h)

**soil_tepmerature_0_to_7cm:** Average temperature of different soil levels below ground. (°C)

**soil_moisture_0_to_7cm:** Average soil water content as volumetric mixing ratio at 0-7, 7-28, 28-100 and 100-255 cm depths. (m³/m³)
is_day: 1 if it is day and 0 if it is night.

**sunshine_duration:** Number of seconds of sunshine of the preceding hour per hour calculated by direct normalized irradiance exceeding 120 W/m², following the WMO definition. (s)

**direct_radiation:** Direct solar radiation as average of the preceding hour on the horizontal plane and the normal plane (perpendicular to the sun). (W/m²)

**diffuse_radiation:** Diffuse solar radiation as average of the preceding hour. (W/m²)
