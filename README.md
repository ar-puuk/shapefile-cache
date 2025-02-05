# shapefile-cache

Shapefiles that are no longer accessible via the census servers.

## What is the problem?

Numberous shapefiles for a variery of geographies use to be available under 
https://www2.census.gov/geo/tiger but as of Feb. 3, 2025, everything under there
returns a 403. See, for example,
https://www2.census.gov/geo/tiger/GENZ2023/shp/cb_2023_us_all_500k.zip.

## Recovering cached files

[censusdis](https://github.com/censusdis/censusdis) loads shapefiles as needed by
users and caches them locally
in the directory `~/.censusdis/data/shapefiles`. If you use `censusdis` regularly,
that directory will contain all the shapefiles you need, provided your research
does not extend to geographies you have not used before.

The purpose of this repository is to allow people to contribute the files they have
cached to a central repo where everyone can take advantage of them. The situation is
fluid and we do not know when or if the shapefiles might become available from the 
census again. 

For the moment, this repo is being used to enable the test workflows of 
[censusdis](https://github.com/censusdis/censusdis) to run.

## Contributing

**First and most important step: back up the contents of your local `~/.censusdis/data/shapefiles`
directory.** Put a copy somewhere safe in the cloud. Put it two places even. Be
very careful before you manually move any files in or out of this directory. Don't risk
losing what you have already cached if you make a mistake.

More to come here, but the first step is very important.
