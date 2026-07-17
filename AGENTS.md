# Repository Guidelines

**Please use Simplified Chinese for all communication. All documentation and comments within the codebase must be written in English.**

## Project Structure & Module Organization

- `Sources/SelectedTextKit/` contains the library code, organized by feature area: `Core`, `TextSelection`, `Accessibility`, `AppleScript`, `Pasteboard`, `AXSwift`, and `Utilities`.
- `SelectedTextKitExample/` is the SwiftUI demo app used for local validation and manual testing.
- `SelectedTextKitExampleTests/` holds test suites for AppleScript, pasteboard, and text-selection behavior.
- `Package.swift` defines package targets and dependencies (`AXSwift`, `KeySender`).

## Build, Test, and Development Commands

- `swift package resolve` installs/updates SwiftPM dependencies.
- `swift build --target SelectedTextKit` builds the library target only (fastest sanity check).
- `swift build` builds all package targets, including the demo app target.
- `open SelectedTextKitExample.xcodeproj` opens the example app in Xcode.
- `xcodebuild -project SelectedTextKitExample.xcodeproj -scheme SelectedTextKitExample -destination 'platform=macOS' build` builds the app from CLI.
- `xcodebuild -project SelectedTextKitExample.xcodeproj -scheme SelectedTextKitExample -destination 'platform=macOS' test` runs tests.

## Coding Style & Naming Conventions

- Use Swift 5.9+ conventions with 4-space indentation.
- Types use `UpperCamelCase`; functions/properties use `lowerCamelCase`; test files end with `Tests.swift`.
- Prefer `async/await` and typed errors (`SelectedTextKitError`) over ad-hoc error handling.
- Follow existing file organization and `// MARK:` sections for readability.
- No repo-level formatter/linter config is currently enforced; match surrounding style in edited files.

## Testing Guidelines

- Tests use Swift Testing (`import Testing`, `@Test`, `#expect`) rather than XCTest assertions.
- Add focused tests for new strategy branches, error paths, and pasteboard/AppleScript edge cases.
- Keep tests deterministic where possible; browser/AppleScript tests may require local app permissions and should be clearly documented in PR notes.

## Commit & Pull Request Guidelines

- Follow the existing Conventional Commit pattern: `type(scope): summary` (examples: `feat(ax): ...`, `fix(pasteboard): ...`, `docs(readme): ...`).
- Keep commits scoped and atomic; avoid mixing refactors with behavior changes.
- PRs should include: purpose, key changes, verification steps/commands, and screenshots when the demo UI or permissions flow changes.
