##notes (draft)

ZIP code boundaries downloaded from US Census TIGER/Line files located at ftp://ftp2.census.gov/geo/tiger/TIGER2014/ZCTA5/tl_2014_us_zcta510.zip

The ZIP code boundaries only come bundled in a national file, so everything outside California needed to be removed. Sadly, I could not find a field in the national file that I could use to identify a California ZIP code. I was facing a process... and the steps turned out to be as follows: 

1. Locate a file that categorized ZIP codes by state. Another census file was used, which can be found here: http://www2.census.gov/geo/docs/maps-data/data/rel/zcta_county_rel_10.txt. 

2. Use OpenRefine to filter out just the records describing ZIP codes in California. The FIPS code for California is '06'. The resulting CSV file can be found here. 

3. (lazy alert) Use the Sublime text editor to transform the CSV from #2 into a single string of ZIP codes. I used these regular expressions with find and replace to create the string: FIND: (.....)(,)(.*)(\n) REPLACE ALL: '$1'$2 

4. From the command line, use ogr2ogr to transform the national ZIP code file into a GeoJSON file. Include a parameter to filter out only the features needed for California. Use the string of California ZIP codes prepared in step #3 in that parameter. The entire command can be found here.

Resulting geoJSON file can be found here.