# Upstream review

Based on karma-firefox-launcher@2.1.3, source [3a7e41ed2aa9f0e811e11aae6633151de6d7708f](https://github.com/karma-runner/karma-firefox-launcher/commit/3a7e41ed2aa9f0e811e11aae6633151de6d7708f). The registry gitHead source manifest contains the previous semantic-release version, but every upstream published runtime file matches this commit byte-for-byte. Only package metadata differs in the upstream tarball, whose integrity was checked independently.

## Issue triage (2026-09-29)

- [#183: Snap temporary-directory access](https://github.com/karma-runner/karma-firefox-launcher/issues/183): Keep original profile/path configuration. Headless smoke uses a directly installed Firefox binary, so it does not claim to repair snap restrictions.
- [#245: Browser capture in containers](https://github.com/karma-runner/karma-firefox-launcher/issues/245): Run the launcher with real Firefox headless and bounded capture timeout.
- [#57: Firefox binary not included](https://github.com/karma-runner/karma-firefox-launcher/issues/57): The browser remains an external prerequisite; the fork does not bundle browser binaries.

No upstream maintainer was contacted. Runtime files and original license/authorship are retained. Development tooling uses Node24; package engine declarations remain unchanged.

## Verification

`npm ci --ignore-scripts`, `npm test`, `npm run test:package`, `npm audit --audit-level=low`. Packed tests install the actual archive and exercise the exported plugin. Publication uses the exact CI tarball only after CI and CodeQL succeed.
