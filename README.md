# AA-SI_metadata
The AA-SI is developing a metadata database that will assist with searching, querying, and accessing acoustic data from NCEI, on-premise, and OMAO storage. We anticipate expanding this database to contextual data.

## Kongsberg EK80 Metadata
Metadata that are extracted from the <con0> header for each .raw file. The <con0> section contains information pertinent to the data file as a whole.
| Variable                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|test|<con0>|test variable|NA|NA|1|

## Kongsberg EK60 Metadata
Metadata that are extracted from the <CON0> header for each .raw file. Every file has a <CON0> telegram at the beginning of the file. The <CON0> section contains information pertinent to the data file as a whole.
| Variable                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|ConfigurationTransducer|<CON0>||List of transducers|NA|NA|1|

1. Simrad EK60 Scientific Echo Sounder Instruction Manual. Copyright 2001.
n. [Anderson, V. C. 1950. Sound scattering from a fluid sphere. JASA. 22(4): 426-431](https://doi.org/10.1121/1.1906621)
