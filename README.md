# Scrapsy

This repository fetches [Paris' Velib](https://www.velib-metropole.fr/) live data every 30 s from this [Paris Open data's API](https://opendata.paris.fr/explore/dataset/velib-disponibilite-en-temps-reel/information/) and stores it.

:exclamation: The API seems to gives sometime data from a random timestamp close to time of request. (it can give you the data from 3 minutes before your request time even though new data is available)

## Data description

Every snapshot is stored in a `.csv` file named by the timestamp of the data (Unix time).

Example of snapshot `1658398440.csv` (Thursday 21 July 2022 10:14:00)

| station_code | mechanical_available | electric_available  |
| --- | ---:| ---:|
| 16107 | 0 | 2 |
| 5001  | 3 | 4 |
| 10013 | 1 | 1 |
| ...   |...|...|


| Variable | Description |
| --- | --- |
| `station_code`| Velib station identifier |
| `mechanical_available` | number of mechanical bicycle (green) available at this time at this station |
| `electric_available`   | number of electric bicycle (blue) available at this time at this station |


This table is used together whith `stations.json`


| station_code | name | latitude | longitude | capacity | is_installed | is_renting | is_returning | town |
| --- | --- | ---: | ---: | ---: | ---:  | ---: | ---: | --- |
|16107|	Benjamin Godard - Victor Hugo|48.865983  |2.275725   |35|1|1|1|Paris|
| ... | ... | ... | ... | ... | ...  | ... | ... | ... |
|5001 |Harpe - Saint-Germain         |48.85151882|2.343670316|45|1|1|1|Paris|
|10013|Alibert - Jemmapes            |48.87104405|2.366104462|60|1|1|1|Paris|
| ... | ... | ... | ... | ... | ...  | ... | ... | ... |


| Variable | Description |
| --- | --- |
| `station_code`| Velib station identifier |
| `name`        | name of the station |
| `latitude`    | latitude of the station |
| `longitude`   | longitude of the station |
| `capacity `   | total number of docks of the station |
| `is_installed`| 1 if the station is deployed and working, 0 otherwhise |
| `is_renting`  | 1 if the station can rent bicycles, 0 otherwhise |
| `is_returning`| 1 if bicycles can be parked at the station, 0 otherwhise (independently of docks availability) |
| `town`        | town of the station|
