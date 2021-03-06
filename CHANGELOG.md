# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.7.1] 2020-06-17
### Added
- API: endpoint for fetching multiple streams by uuid
- PULL: use correct user agent

### Fixed
- CACHE: shorter keys to make memcached work

## [0.7.0] 2020-06-15
### Added
- API: Response caching with builtin, redis and memcached

### Changed
- LOG: Ignore content-type nothing in requests

## [0.6.16] 2020-05-27
### Fixed
- METRICS: do not expose search information in call counts

## [0.6.15] 2020-05-27
### Added
- Support for JSON log format
- Show api call timing information in log file
- Split up api calls in prometheus endpoint with tags

### Fixed
- CLI: Verbose did not work
- Fixed station voting from IPv6 address (Fixed: #69)

### Changed
- DEPENDENCY: Use fern logger instead of env_logger
- API: Use limit parameter if limit is not otherwise provided (Fixed: #64)

### Removed
- API: Old style click count from metrics

## [0.6.14] 2020-04-13
### Fixed
- PLS files had title and file content reversed

## [0.6.13] 2020-04-13
### Fixed
- Always add CORS header, even on errors

### Added
- Answer OPTIONS requests for better support of CORS

## [0.6.12] 2020-04-12
### Added
- METRICS: station_clicks, api_calls
- API: codec parameter to advanced search

### Fixed
- Use utc timestamp for clicks in database

## [0.6.11] 2020-02-17
### Added
- API: Added stationuuid to m3u output

### Fixed
- API: Filter order column for extra tables

## [0.6.10] 2020-02-01
### Fixed
- API: Wrong links in docs
- API: Faster select from stationcheck view with added index
- SYNC: Only update stations with changed votes
- SYNC: Faster update of station's clicks with added index

## [0.6.9] 2020-02-01
### Added
- DEB: logrotate config
- API: more exports to metrics
- API: config endpoint

### Fixed
- API: return change lists (stations, checks, clicks) from start if lastuuid not found

### Changed
- CLEANUP: remove all non http/https content from favicon field of stations
- ANSIBLE: disabled all apache2 logging by default
- CONFIG: type errors do not get ignored with default value
- CONFIG: use human readable durations instead of fixed seconds or hours

## [0.6.8] 2020-01-22
### Fixed
- Fixed wrong sql delete
- Ignore station checks and clicks on pull, when there is no station

### Added
- Show "hidebroken" in docs for station query

## [0.6.7] 2020-01-19
### Fixed
- Migrations on mysql

## [0.6.6] 2020-01-19
### Added
- Simple sync of votes, may drop some votes

### Fixed
- Broken stations were not marked
- Make foreign keys of StationClick and StationCheckHistory on delete cascade

## [0.6.5] 2020-01-18
### Added
- Ansible role and example playbook for debian/ubuntu

### Fixed
- Station checks
- Always use UTC time in database
- Faster check insert with mysql 5.7

### Changed
- Default install paths changed
- IPs for clicks are only kept until not needed anymore (default 24 hours)

## [0.6.4] 2020-01-14
### Fixed
- Insert of checks does now ignore duplicates
- Resuse checkuuids of pullserver, do not generate new ones on pull
- Incremental results of /format/stations/changed, /format/checks and /format/clicks do work reliably

### Changed
- Replaced StationCheck table with view on StationCheckHistory
- Migration deletes contents of StationCheckHistory, to remove unconnected uuids
- Migration deletes contents of PullServers to force re-pulling of every server

## [0.6.3] 2020-01-12
### Added
- Script for building distribution file

### Changed
- Debian package
- Improved readme

## [0.6.2] 2020-01-11
### Added
- Sync for clicks
- Api for clicks /format/clicks

### Changed
- Document "/format/url" endpoint as station click endpoint
- Document returned structs "station", "checks"
- Faster sync

### Fixed
- Clickcount calculation for each station
- Error in /format/stations/changed endpoint

## [0.6.1] 2020-01-08
### Added
- Prometheus docs

### Fixed
- SQL error in endpoint /checks?seconds=x
- Database column mixup for state and language

### Changed
- Run as non root user in docker by default

## [0.6.0] - 2020-01-06
### Added
- Changelog
- Check fields: "metainfo_overrides_database", "public", "name", "description", "tags", "countrycode", "homepage", "favicon", "loadbalancer"

### Removed
- "id" from all of the API, because database id should not be exposed
- Endpoint /stations/broken 

### Changed
- Faster station import from pull source
- Restructured more code to the new style of connecting to the database, this should enable other types of databases (e.g.: postgresql) on the long term, this means also more error checking and use of transactions.

### Fixed
- Output lastchangetime and countrycode in /json/stations/changed
- Correctly collect and summarize different sources of station checks
- "numberofentries" added to pls output
- Less usages of "unwrap()"

## [0.5.1] - 2019-12-11
### Added
- "url_resolved" field to station lists
- "random" order to station lists

### Removed
- "negativevotes" field from station lists

### Fixed
- Fixed json result of vote endpoint
- Clean up tag and language fields on import
- Documentation cleanup and extensions

## [0.5.0] - 2019-12-08
### Added
- First documented release :)
