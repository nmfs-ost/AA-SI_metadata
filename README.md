# AA-SI_metadata
The AA-SI is developing a metadata database that will assist with searching, querying, and accessing acoustic data from NCEI, on-premise, and OMAO storage. We anticipate expanding this database to contextual data.

## Kongsberg EK80 Metadata
Metadata that are extracted from the CON0 header for each .raw file. The <con0> section contains information pertinent to the data file as a whole.
| Variable                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|test|CON0|test variable|NA|NA|EK80[^1]|
[^1]: [EK80 Data Formats](https://github.com/nmfs-ost/AA-SI_metadata/blob/main/ek80_interface_en_us_file-formats.pdf)  

## Kongsberg EK60 Metadata
### CON0
Metadata that are extracted from the CON0 header for each .raw file. Every file has a CON0 telegram at the beginning of the file, which contains information pertinent to the data file as a whole.
| Variable                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|ConfigurationTransducer|CON0:ConfigurationDatagram|I'm not sure this is read?|NA|NA|EK60[^2]|
|SurveyName|CON0:ConfigurationHeader|Cruise/Survey Name/ID. Input by the user. The data string may or may not exist depending on whether it was input by the user.|NA|NA|EK60[^2]|
|TransectName|CON0:ConfigurationHeader|Transect Name/ID. Input by the user. The data string may or may not exist depending on whether it was input by the user.|NA|NA|EK60[^2]|
|SounderName|CON0:ConfigurationHeader|Echosounder Name/ID. Input by the user. May be "EK60". The data string may or may not exist depending on whether it was input by the user.|NA|NA|EK60[^2]|
|TransducerCount|CON0:ConfigurationHeader|The number of transducers which have data in the file. Input by the user?|NA|NA|EK60[^2]|
|ChannelID|CON0:ConfigurationTransducer|The channel ID. Each data stream has a separate channel and the channel IDs are unique within a file.|NA|NA|EK60[^2]|
|BeamType|CON0:ConfigurationTransducer|The beam type. 0=single beam. 1=split beam.|NA|NA|EK60[^2]|
|Frequency|CON0:ConfigurationTransducer|The transmit frequency of the channel in Hz.|NA|NA|EK60[^2]|
|PulseLengthTable|CON0:ConfigurationTransducer|List of possible pulse durations in seconds. Do we need this?|NA|NA|EK60[^2]|
[^2]: [EK60 Data Formats](https://github.com/nmfs-ost/AA-SI_metadata/blob/main/EK60_reference_manual_data-formats.pdf)
