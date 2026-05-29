# Changelog

All notable changes to this project are documented here.

## [3.0.0] - 2026-05-29

### Removed

- Removed all external model API execution.
- Removed credential setup and credential persistence instructions.
- Removed the API client script and the now-unused `scripts/` directory.
- Removed mixed native/external execution strategy.

### Changed

- Simplified execution to two strategies: native multi-model and serial multi-perspective.
- Updated `SKILL.md` with clearer trigger boundaries and no external dependency.
- Updated prompt and report templates to match the two-strategy workflow.
- Updated Chinese and English README files with the new behavior and removal impact.
- Updated examples to avoid non-native model assumptions.

## [2.2.0] - 2026-04-15

### Added

- Batch prompt file support and retry support for the previous API client.
- Placeholder documentation for prompt templates.

### Changed

- Improved report templates and installation documentation.

## [2.1.0] - 2026-04-15

### Added

- Added external model API evaluation in the previous workflow.

### Changed

- Added automatic fallback between multiple evaluation strategies.

## [2.0.0] - 2026-04-14

### Added

- Multi-model cross-validation.
- Peer review between evaluators.
- Final arbitration with consensus indicators.
- Serial multi-perspective fallback.

## [1.0.0] - 2026-04-13

### Added

- Initial eight-dimension Skill evaluation framework.
- Weighted scoring and S/A/B/C/D grades.
- Multi-Skill comparison support.
