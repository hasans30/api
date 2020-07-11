# COVID19-India API

A volunteer-driven, crowd-sourced database for COVID-19 stats & patient tracing in India.

[Source Code on Github](https://github.com/covid19india/api)

## About Raw Data

Raw Data is split into multiple files. You can regenerate the full raw data by merging the following json files.

`api.covid19india.org/raw_data1.json` (Data till EoD Apr 19th)<br>
`api.covid19india.org/raw_data2.json` (Data till EoD Apr 26th)<br>
`api.covid19india.org/raw_data3.json` (Data till EoD May 09th)<br>
`api.covid19india.org/raw_data4.json` (Data till EoD May 23rd)<br>
`api.covid19india.org/raw_data5.json` (Data till EoD Jun 04th)<br>
`api.covid19india.org/raw_data6.json` (Data till EoD Jun 19th)<br>
`api.covid19india.org/raw_data7.json` (Data till EoD Jun 30th)<br>
`api.covid19india.org/raw_data8.json` (Data till EoD Jul 07th)<br>
`api.covid19india.org/raw_data9.json` (Live 🚀)<br>

Raw Data 1 and 2 are organized at a patient level. i.e., there is one row per person. The deaths and recoveries that happened during that time need to be fetched from deaths_and_recoveries{1,2} json files.

From Raw Data 3 onwards, structure has been changed to accomadate both aggregate as well as patient level entries.

1. If patient level information is available (from several states like KA,BH etc.), that is captured at one row per patient.
2. If only district-wise information is available, one row is entered for each district, and "numcases" field mentions the number of cases in that district.
3. If only state-wise information is available, one row is added added for the entire state
4. Recoveries and Deceased information is also  also present in raw_data. Use the "Current Status" field to extract that information.

All other aggregate APIs retain the same behaviour.
CSV files for the same are also available through `api.covid19india.org/csv/latest/raw_data{n}.csv`

We are working towards providing a singular raw_data that can be the source of truth. However, we strongly advise you to use the aggregate information for any analysis.


### JSON

| Status        | Data                                                                      | URL                                                      |
| ------------- | ------------------------------------------------------------------------- | -------------------------------------------------------- |
| :green_heart: | Patient Level : Raw Data Partition 1 (Till Apr 19)                        | https://api.covid19india.org/raw_data1.json              |
| :green_heart: | Patient Level : Raw Data Partition 2 (From Apr 20 to Apr 26)              | https://api.covid19india.org/raw_data2.json              |
| :green_heart: | Patient Level : Raw Data Partition 3 (From Apr 27 to May 09)              | https://api.covid19india.org/raw_data3.json              |
| :green_heart: | Patient Level : Raw Data Partition 4 (From May 10 to May 23)              | https://api.covid19india.org/raw_data4.json              |
| :green_heart: | Patient Level : Raw Data Partition 5 (From May 24 to Jun 04)              | https://api.covid19india.org/raw_data5.json              |
| :green_heart: | Patient Level : Raw Data Partition 6 (From Jun 05 to Jun 19)              | https://api.covid19india.org/raw_data6.json              |
| :green_heart: | Patient Level : Raw Data Partition 7 (From Jun 20 to Jun 30)              | https://api.covid19india.org/raw_data7.json              |
| :green_heart: | Patient Level : Raw Data Partition 8 (From Jul 01 to Jul 07)              | https://api.covid19india.org/raw_data8.json              |
| :green_heart: | Patient Level : Raw Data Partition 9 (From Jul 08th onwards)              | https://api.covid19india.org/raw_data9.json              |
| :green_heart: | National Level :Time series, State-wise stats and Test counts             | https://api.covid19india.org/data.json                   |
| :green_heart: | State Level : has district-wise info                                      | https://api.covid19india.org/state_district_wise.json    |
| :green_heart: | State Level : Daily changes                                               | https://api.covid19india.org/states_daily.json           |
| :green_heart: | State Level : Testing data                                                | https://api.covid19india.org/state_test_data.json        |
| :green_heart: | National/State/District Level : Latest cumulative/daily counts            | https://api.covid19india.org/v3/data.json                |
| :green_heart: | National/State/District Level : Old per-date cummulative/daily counts     | https://api.covid19india.org/v3/data-{YYYY-MM-DD}.json   |
| :green_heart: | National/State/District Level : All dates cumulative/daily counts         | https://api.covid19india.org/v3/data-all.json            |
| :green_heart: | National/State Level: Timeseries _(different structure)_                  | https://api.covid19india.org/v3/timeseries.json          |
| :green_heart: | District Level : Daily changes                                            | https://api.covid19india.org/districts_daily.json        |
| :end:         | District Level : Zones                                                    | https://api.covid19india.org/zones.json                  |
| :end:         | Essentials and resources                                                  | https://api.covid19india.org/resources/resources.json    |
| :end:         | Raw Data (Partition 1 + Partition 2. Frozen after Apr 26th)               | https://api.covid19india.org/raw_data.json               |
| :end:         | Deaths and Recoveries (Frozen after Apr 26th)                             | https://api.covid19india.org/deaths_recoveries.json      |
| :end:         | Travel history (No more updated)                                          | https://api.covid19india.org/travel_history.json         |

### CSV

Sometimes, having files in a spreadsheet format is more useful for analysts and scientists. We have provided the files as downloadable csv files at the following location.

| Data                 | URL                                                                    |
| -------------------- | ---------------------------------------------------------------------- |
| Google sheets in CSV | [https://api.covid19india.org/csv/](https://api.covid19india.org/csv/) |

> :rocket: Quick example : Apply the formula `=IMPORTDATA("https://api.covid19india.org/csv/latest/state_wise.csv")` in A1 cell of a Google Sheets to get the state data for analysis :)


### Alternate API's by Contributors
API for current cases, state-wise, district-wise and historical data of India COVID-19
- Graphql playground - https://covidstat.info/graphql [API documentation](https://github.com/COVID19-SARS-CoV-2/web-covid-api/blob/master/india_apis.md)

## How this works

- Data in this repository is generated from Google Sheets (https://api.covid19india.org/csv)
- Volunteers collect data from trusted sources and update the sheet
- We use Github Actions to periodically fetch the data from the sheet to the repo
- Static json and csv files into the gh-pages repository
- gh-pages serve the json files just like a website

## License
This repository contains both the code that routinely fetches the data from Google Sheet and convert it into JSON files in the required format and the data itself (in the gh-pages branch). So, the content of this repository is licensed in two ways : Code and Data
License for Code (Consider this as everything in the `master` branch) : MIT License (Detailed in LICENSE_CODE.txt)
License for Data (Consider this as everything in the `gh-ages` branch) : CC-BY-SA-4.0 License (Detailed in LICENSE_DATA.txt)

## Contributing

- Contributions to new data formats are welcome. Please create a GH issue and discuss there before working on the same
- Please raise an issue before submitting a PR
- Report issues regarding [covid19india.org](https://www.covid19india.org) website in the [react-site repository](https://github.com/covid19india/covid19india-react/issues)
- DO NOT change anything in `gh-pages` branch directly as they get replaced automatically


## Quick Links

- [Telegram Group](https://telegra.ph/CoVID-19--India-Ops-03-24)
- [Sources Considered](https://telegra.ph/Covid-19-Sources-03-19)


-----


## Projects Using This API

- [COVID-19 INDIA TRACKER](https://www.covid19india.org/) (Main Dashboard)
- [covid19india.org Ops Telegram Channel](https://t.me/covid19indiaorg) (News and Announcements from covid19india.org Team)
- [covid19india.org Instant Updates](https://t.me/covid19indiaorg_updates) (Instant Updates of new cases added - from covid19india.org Team)

### Some other categories of projects using this API:

- [Analysis](projects/analysis.md)

- [Bots (Discord, Reddit, Telegram, etc.)](projects/bots.md)

- [Browser extensions](projects/browser_extensions.md)

- [Mobile apps](projects/mobile_apps.md)

- [Other trackers/dashboards](projects/miscellaneous.md)

...........................................
