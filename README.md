
# shapefile-cache

Shapefiles that are no longer accessible via the census servers.

## What is the problem?

Numberous shapefiles for a variery of geographies use to be available under https://www2.census.gov/geo/tiger
but as of Feb. 3, 2025, everything under there returns a 403. See, 
for example, https://www2.census.gov/geo/tiger/GENZ2023/shp/cb_2023_us_all_500k.zip.

Recovering cached files censusdis loads shapefiles as needed by users and caches them locally in the
directory ~/.censusdis/data/shapefiles. If you use censusdis regularly, that directory will contain all
the shapefiles you need, provided your research does not extend to geographies you have not used before.

The purpose of this repository is to allow people to contribute the files they have cached to a central
repo where everyone can take advantage of them. The situation is fluid and we do not know when or if the
shapefiles might become available from the census again.

For the moment, this repo is being used to enable the test workflows of censusdis to run.

## Contributing

First and most important step: back up the contents of your local ~/.censusdis/data/shapefiles directory. Put a copy somewhere safe in the cloud. Put it two places even. Be very careful before you manually move any files in or out of this directory. Don't risk losing what you have already cached if you make a mistake.

### Install git-lfs

Some of the shapefiles in this repo are very large and need to be stored in Git Large File Storage. If
you don't already have it installed, please do so. There are installers for MacOS and Windows and various
flavors of Linux.

### Clone the repo

Now, clone this repo and enter the newly checked out directory. You can do this in ~/src or wherever you
normally check out repos.

```shell
git clone https://github.com/censusdis/shapefile-cache.git
cd shapefile-cache
```

Now, just to be sure before you move on. Make sure you did not skip the first step.
Make sure you have everything in your `~/.censusdis/data/shapefiles` backed up.
Do not pass go, do not collect $200.

Now there are two things you can do, you can either sync shapefiles from the repo into your local
cache or sync your local cache into the repo, or both.

### Sync shapefiles from the repo

Assuming you are in the `shapefile-cache` directory you just cloned, you can put everything that is in the repo but that you do not have in your cache into your cache with the command

```shell
rsync -r --ignore-existing shapefiles ~/data
```

This will sync any files in the repo you just checked out that don't exist in your cache to your cache.

### Sync shapefiles from your cache to the repo

You may have locally cached shapefiles that are not yet in the repo. If so, we would love for you to contribute them.

First, do an rsync in the opposite direction of the one we just did.

```shell
rsync -r --ignore-existing ~/data/shapefiles .
```

Now let's see if there were any updates:

```shell
git status
```

If the results are empty, then the repo already has everything you have. If not, then you have something to contribute. 

### Sync to a fork and submit a PR

To contribute your shapefiles back, you will need to fork the repo, then check out your fork with

```shell
git clone https://github.com/{my-username}/shapefile-cache.git shapefile-cache-clone
cd shapefile-cache-clone
```

Now you can do the sync again

```
rsync -r --ignore-existing ~/data/shapefiles .
git status
```

This should show you your updates again, but this time you can git commit and git push them and then
open a PR so we can merge them into the base repo.

## Questions or Comments?

Please open an issue or discussion in this repo.
