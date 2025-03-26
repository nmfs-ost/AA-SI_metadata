# AA-SI_metadata
The AA-SI is developing a metadata database that will assist with searching, querying, and accessing active acoustic data that have been copied from NCEI, on-premise, or OMAO storage to our Google cloud storage bucket. We anticipate expanding this database to contextual data in the future. Our metadata follow the ICES active acoustic metadata convention [AcMeta](https://github.com/ices-publications/AcMeta) to the extent possible. We will work with the AcMeta community to update metadata when needed.  
  
We separate our metadata into to general categories: **project** and **file**. The project-level metadata describe the mission, cruise, and platform attributes, which can be used to search for data that were collected during specific surveys or by specific institutions. File-level metadata describe the instruments and data attributes, which can be used to search for data that were collected at specific frequencies, with specific echosounder models, or different states, such as active narrowband or passive wideband.  
  
For a number of attributes, we will need to define controlled vocabulary and/or follow [ICES controlled vocabulary](https://vocab.ices.dk/?ref=311). This may entail creating lookup tables.

## Project Attributes
| Attribute                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|mission_name|OMAO cruise instructions or NCEI Cruisepack|The full name for the program/project that was responsible for collecting the data.|Mission: mission_name|NA|AcMeta[^3][^4]|
|mission_id|OMAO cruise instructions or NCEI Cruisepack|An identifier, e.g., acronym or short name, for the program/project that was responsible for collecting the data.|Mission: mission_id|NA|AcMeta[^3][^4]|
|institution|OMAO cruise instructions or NCEI Cruisepack|The Acronym or full name for the Institution that was responsible for collecting the data.|Mission: institution|NA|AcMeta[^3][^4]|
|cruise_id|OMAO cruise instructions or NCEI Cruisepack|The cruise identifier. In NOAA, it is often a two-character ship identifier, two-digit year, and two-digit sequential cruise number for that ship. For example, the third cruise on the Henry B Bigelow in 2025 is HB2503.|Cruise: cruise_id|NA|AcMeta[^3][^4]|
|cruise_start_date|date and time of first data file recorded *or OMAO cruise instructions?*|ISO 8601 format including local time zone|Cruise: cruise_start_date|NA|AcMeta[^3][^4]|
|cruise_end_date|date and time of last data file recorded *or OMAO cruise instructions?*|ISO 8601 format including local time zone|Cruise: cruise_end_date|NA|AcMeta[^3][^4]|
|platform_name|OMAO cruise instructions|Full name for the platform that collected the data. For example, the NOAA ship Henry B Bigelow can be listed as "Henry B. Bigelow" or "Henry B Bigelow" *multiple names suggest a need for controlled vocabulary*|Platform: platform_name|NA|AcMeta[^3][^4], ICES[^5]|
|platform_code|Controlled vocabulary lookup table and/or NCEI Cruisepack|Abbreviated code for the platform. Link to the ICES controlled vocabulary and/or link to the cruise_id in the cruise attributes. For example, the NOAA ship Henry B Biglow can be abbreviated as "HB", "HBB", "HB Bigelow", or "HBBigelow". *this is why we need controlled vocabulary*|Platform: platform_code|NA|AcMeta[^3][^4], ICES[^5]|

## File Attributes
Controlled vocabulary for instrument_transceiver_manufacturer and instrument_transceiver_model  
These link to each data file
| Attribute                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|instrument_frequency|original data file or netCDF file *or NCEI Cruisepack?*|acoustic center frequency for continuous wave/narrowband (CW). Include minimum and maximum frequencies for wideband (WB). Units of kHz. Provide as a Python list, such as \[38.0, NA, NA\] for CW or \[70.0, 50.0, 90.0\] for WB.|Instrument: instrument_frequency|NA|AcMeta[^3][^4]|
|instrument_transceiver_manufacturer|original data file or netCDF file *or NCEI Cruisepack?*|Manufacturer of the sonar. *controlled vocabulary?*|Instrument: instrument_transceiver_manufacturer|NA|AcMeta[^3][^4]|
|instrument_transceiver_model|original data file or netCDF file *or NCEI Cruisepack?*|Model of the sonar. *controlled vocabulary?*|Instrument: instrument_transceiver_model|NA|AcMeta[^3][^4]|
|calibration|*NCEI Cruisepack or where?*|Calibration state: "Yes" or "No"|Calibration: calibration|NA|AcMeta[^3][^4]|
[^3]: [AcMeta](https://github.com/ices-publications/AcMeta)
[^4]: [AcMeta IO page](https://htmlpreview.github.io/?https://github.com/ices-publications/AcMeta/blob/master/Formatted_docs/TG-AcMeta.html)
[^5]: [ICES Ship/Platform Vocabulary](https://vocab.ices.dk/?ref=311)

## Kongsberg EK80 Metadata
Metadata that are extracted from the \<Configuration\> XML header for each .raw file. The \<Configuration\> section contains information pertinent to the data file as a whole.
| Attribute                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
|--------------------------------------|---------|-------------|--------|--------------|------------|
|test|CON0|test variable|NA|NA|EK80[^1]|
[^1]: [EK80 Data Formats](https://github.com/nmfs-ost/AA-SI_metadata/blob/main/ek80_interface_en_us_file-formats.pdf)  

## Kongsberg EK60 Metadata
### CON0
Metadata that are extracted from the CON0 header for each .raw file. Every file has a CON0 telegram at the beginning of the file, which contains information pertinent to the data file as a whole.
| Attribute                             | Source  | Description | AcMeta | SonarnetCDF4 | References |
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
