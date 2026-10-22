# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [4.1.0] - 2026-10-22

### Added

- `Compiler.Parse.Variable` now exposes several predicate functions that can be helpful in parsing

### Fixed

- `SemanticVersion.fromString` erronously succeeded when the string contained more than three parts, but only three were numbers, like in `1.x.2.3`
- `ModuleName.fromString` now allows underscores and unicode letters.

## [4.0.0] - 2026-10-18

### Fixed

- Accept the same upper- and lowercase variable names that the haskell based parser does
- Top-level declarations now has to start at column 1
- More accurate calculation of large hex digits
- Parser now correctly parses expressions like `{ r | a = 1 }.a`
- Fixed a bug where the parser would consider multiple arguments to a custom type variant, to be args to the first argument
- Fixed a bug where if the non-first argument to a function started with `as`, it would fail to compile
- Fixed a bug where `as` in when branch guards wasn't recognized unless the entire pattern was wrapped in parenthesis
- Correct start position of `import`, `type`, `type alias` and `port` declarations 

## [3.0.0] - 2026-06-22

### Added

- `Pattern.topLevelParser` parses exactly one pattern, as opposed to _one or more_. It's less conservative
in cases like `Ctor one`, where `Pattern.parser` will parse two patterns

### Changed

- Blank lines (zero or any number of whitespace characters) are now tolerated in multi-line strings
- `Number.Float` now includes the originally parsed text representation of the `Float`

### Fixed

- `a.accessor` is no longer parsed as `a .accessor`
- Ctor destructuring always consumed the next pattern as an argument. `Ctor one` was parsed as `(Ctor one)`
- Performance increase when parsing comments
- Long operator chains no longer risks stack overflow

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
