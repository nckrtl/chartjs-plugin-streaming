# Changelog

## [3.0.0] - 2025-08-21

### Breaking Changes
- **BREAKING**: Now requires Chart.js v4.0.0 or later (dropped support for Chart.js v3)
- **BREAKING**: Published as scoped package `@nckrtl/chartjs-plugin-streaming`

### Changed
- Updated all dependencies to Chart.js v4 compatible versions
  - `chart.js`: ^4.4.0
  - `chartjs-adapter-luxon`: ^1.3.1
  - `chartjs-plugin-annotation`: ^3.0.1
  - `chartjs-plugin-datalabels`: ^2.2.0
  - `chartjs-plugin-zoom`: ^2.0.1
- Migrated `destroy` plugin hook to `afterDestroy` (Chart.js v4 requirement)
- Updated documentation for Chart.js v4 compatibility
- Updated examples to use Chart.js v4

### Migration Guide
See the [migration guide](docs/guide/migration.md) for detailed instructions on upgrading from v2 to v3.

## Previous Versions
For the changelog of the original package versions, see [https://github.com/nagix/chartjs-plugin-streaming/releases](https://github.com/nagix/chartjs-plugin-streaming/releases)