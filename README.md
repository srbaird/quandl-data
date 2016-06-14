# quandl-data
Scripts and config files for quandl data download

# generate a command to download a list of datasets for all databases
./getDataSets.bsh dbcodes

#unzip all dataset lists in codes
./unpackDatasets.bsh codes > alldatasets

# select datasets
grep ^WIKI alldatasets | cut -d"," -f1 | wc -l

# select from all datasets into dataset files
grep ^COM/ alldatasets >> commodities/datasets_CHRIS

# Spot exchange rates
grep ^BOE alldatasets | grep "\"Spot" > currencies/datasets_BOE_SPOT

# UK interest rates
grep ^BOE/IUD alldatasets  > rates/datasets_BOE_IUD

# Federal reserve interest rates

# Get data sets example
./getData.bsh currencies

# Simple search of rates dataset file
sed 's/^\(.*\),".*ate, \(.*\) into \(.*\)"/\1, \2,\3/g' datasets_
