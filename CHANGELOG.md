# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial public release
- Support for Apache 2.4 on Ubuntu 22.04+
- Virtual host configuration with HTTP and HTTPS support
- SSL/TLS certificate validation
- Per-site log files
- Apache configuration validation before restart
- Comprehensive README with examples
- GitHub Actions CI/CD pipeline
- Automated testing with ansible-lint

### Changed
- Updated to Apache 2.4 syntax (Require directives)
- Replaced deprecated `with_items` with `loop`
- Modernized handler naming conventions

### Fixed
- Fixed service restart loop bug
- Fixed Jinja2 template syntax errors
- Added privilege escalation (become: true) to all tasks

## [1.0.0] - TBD

Initial release
