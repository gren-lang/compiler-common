# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-04-28

### Added

- Module values now has a reference to where the type signature begins, in addition to where the first
type in the type signature starts

### Changed

- `SourcePosition` moved to `Compiler.SourcePosition`
- Nested comments is now supported
- Comments are now represented as an array of `SourcePosition.Located Comment`
- Comment values are no longer trimmed
- Multi-line strings can now contain blank lines without indentation

### Fixed

- Parser can now parse the unicode replacement character literal
- Parsing expressions like `(-a + b)` now works
- Module value names can now start with `type` or `port`
- Fix source position of `Ast.Access`
- Fix source position module values, with or without type signatures

## [1.0.0] - 2026-03-22

- First release
