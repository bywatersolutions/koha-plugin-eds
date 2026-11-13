# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
This is ByWater Solutions' build of [EBSCO's EDS plugin](https://github.com/ebsco/edsapi-koha-plugin): each version is EBSCO's version with a "-bws" suffix, plus the changes listed here.

## [Unreleased]

### Changed
- Koha's plugin list now shows the release's version, such as 25.11.001-bws.2, instead of EBSCO's 25.11001 for every ByWater build.

## [25.11.001-bws.2] - 2026-11-10

### Added
- The EDS results, record detail, advanced search and publication pages now tell search engines not to index them or follow their links.
- The EDS pages and the lookups behind the OPAC search box now turn away requests that no OPAC page makes, such as crawlers opening them directly. A visitor without cookies is sent back once to check that their browser keeps them, and each visitor is limited to 30 EDS pages and 120 lookups a minute.
- On a Koha with the bot guard turned on (opac_bot_guard in koha-conf.xml), the EDS pages and lookups now need the same trust cookie as the rest of the OPAC. A page view without one gets the bot guard's challenge and a lookup without one is refused, while observe mode, exempt addresses and logged in patrons work as they do elsewhere in the OPAC.

### Changed
- OPAC pages no longer fetch the plugin's language file and the Customisation Manager JavaScript separately; both are now part of the page. Customisation Manager JavaScript now runs after the EDS search box is set up.

### Fixed
- Translated labels that contain a colon, such as "Browse by Journal Title:", are no longer cut short.

## [25.11.001-bws] - 2026-11-04

### Changed
- Autocomplete credentials are now fetched on the first keystroke in the search box instead of when the page loads.
- Requests to the EDS API now time out after 30 seconds instead of 180.

### Fixed
- OPAC pages no longer start an eds-raw.pl process on every view for visitors without browser session storage, such as headless crawlers, which could use up a server's memory. The search fields are now part of the page.

[Unreleased]: https://github.com/bywatersolutions/koha-plugin-eds/compare/v25.11.001-bws.2...HEAD
[25.11.001-bws.2]: https://github.com/bywatersolutions/koha-plugin-eds/compare/25.11.001-bws...v25.11.001-bws.2
[25.11.001-bws]: https://github.com/bywatersolutions/koha-plugin-eds/releases/tag/25.11.001-bws
