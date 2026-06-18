# Changelog: ftw-pki-clntsrvr

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.0.3] - 2026-06-18

### Added
- Refactor CLI-handling and PKI-container integration for client-server

### Changed
- Migrate documentation and core logic to CSRWorkflow pattern
- Integrate TomlPreParser into client-server CSR program
- Rename legacy TOML functions to modernize utility interfaces

### Fixed
- Migrate to -dns argument and improve parser robustness

### Documentation
- Standardize configuration flags and namespaces in developer docs


## [0.0.2a1] - 2026-05-18

### Added
- Integrate local `LeafPKIConfig` mapping to handle secure configuration paths and dynamic target evaluations.
- Register combined user documentation tools within the core Sphinx index tree (`index.rst`).

### Changed
- Refactor `prog_client_server_csr` pipelines to utilize modern `ClientServerPolicy` rules and unified configuration mechanisms.
- Migrate and update core module imports to resolve the structurally renamed `cert_request` dependency.
- Adjust automated GitHub Actions CI matrix (`ci.yml`) environments for robust multi-platform execution passes.

### Removed
- **Breaking Change**: Remove legacy static path configurations and drop the unused `platformdirs` runtime mapping block from `conf.py`.

---

## [0.0.1] - 2026-05-18
- Initial commit and package skeleton for the combined client-server CSR tool suite.
