# nyc-public-waterfront

NYC public waterfront (publicly owned land that is touching or near water) location data for all five boroughs.

## Contents

The data is provided in two formats:
 * GeoJSON: `data/geojson/nyc-public-waterfront.geojson`
 * Shapefile: `data/shp/nyc-public-waterfront.shp`

## Methodology

 1. [MapPLUTO](http://www1.nyc.gov/site/planning/data-maps/open-data/dwn-pluto-mappluto.page#mappluto) for each borough was clipped to a 150-foot buffer of [the city's shoreline](https://data.cityofnewyork.us/Recreation/Shoreline/2qj2-cctx).
 2. The data was filtered to only features where `OwnerType` is `C` (city), `X` (mixed, tax exempt), or `O` ("other", including public authorities, state, and federal ownership).
 3. We added a new field, `public`, which is `yes` when the owner is public and `NULL` otherwise.
 4. The data was filtered to only those properties with `public` set to `yes`.
 4. We added a new field, `OwnerFixed`, which attempts to provide a more consistent owner name for each feature. Abbreviations were expanded, capitalization was fixed. This was only done for libraries on property that is publicly owned. Where multiple city agencies were listed in `OwnerName` (eg, "DCAS/DEPARTMENT OF ED"), we chose the agency that was more specific (eg, Department of Education). As many of the owners involved are New York State or New York City agencies, we have included the level of government, too, so "Department of Transportation" became "New York City Department of Transportation".
