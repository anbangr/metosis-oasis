# Changelog

All notable changes to this project will be documented in this file.

## [0.2.6] - 2026-05-18

### Fixed
- Split `reputation_alpha` into separate `reputation_alpha` (settlement multiplier slope) and `reputation_lambda` (EMA smoothing) parameters to prevent unintended coupling between adjudication and settlement logic.

### Added
- RED-gate tests verifying α/λ parameter independence (`test/adjudication/test_reputation_parameters.py`).
- Spec-v0.97 test infrastructure with shared fixtures and constitutional constants (`test/spec_v097/`).
- Additional constitutional parameters: `fairness_minimum`, `protocol_fee_bps`, `reputation_alpha`.

### Changed
- `SanctionEngine.reduce_reputation` now uses `config.reputation_lambda` for EMA smoothing.
- `SettlementCalculator` now uses `config.reputation_lambda` for EMA smoothing.
- Extracted `_compute_ema` helper on `SanctionEngine` for testability.
