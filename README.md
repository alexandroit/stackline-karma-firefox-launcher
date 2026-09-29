# @stackline/karma-firefox-launcher

> A Karma plugin. Launcher for Firefox.

[![npm version](https://img.shields.io/npm/v/@stackline/karma-firefox-launcher.svg?style=flat-square)](https://www.npmjs.com/package/@stackline/karma-firefox-launcher)
[![license](https://img.shields.io/npm/l/@stackline/karma-firefox-launcher.svg?style=flat-square)](https://github.com/alexandroit/stackline-karma-firefox-launcher)
[![GitHub repository](https://img.shields.io/badge/GitHub-alexandroit%2Fstackline-karma-firefox-launcher-181717?style=flat-square&logo=github)](https://github.com/alexandroit/stackline-karma-firefox-launcher)
[![Docs](https://img.shields.io/badge/docs-alexandro.net-0f766e?style=flat-square)](https://alexandro.net/docs/vanilla/karma-firefox-launcher/)
[![Reddit community](https://img.shields.io/badge/community-r%2FStackline-ff4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/r/Stackline/)

**[Documentation](https://alexandro.net/docs/vanilla/karma-firefox-launcher/)** | **[npm](https://www.npmjs.com/package/@stackline/karma-firefox-launcher)** | **[Issues](https://github.com/alexandroit/stackline-karma-firefox-launcher/issues)** | **[Repository](https://github.com/alexandroit/stackline-karma-firefox-launcher)**

**Current package version:** `1.0.1`

---

## Why this package?

`@stackline/karma-firefox-launcher` is the Stackline-maintained distribution of `karma-firefox-launcher@2.1.3`. It is an independent continuation of [karma-firefox-launcher](https://github.com/karma-runner/karma-firefox-launcher); original authors and licenses remain credited below.

## Compatibility

| Item | Value |
| :--- | :--- |
| Package | `@stackline/karma-firefox-launcher@1.0.1` |
| API target | `karma-firefox-launcher@2.1.3` |
| Supported Node.js | `See supported framework requirements` |
| License | `MIT` |
| Main entry | `index.js` |
| Runtime dependencies | `is-wsl, which` |

## Installation

```bash
npm install @stackline/karma-firefox-launcher
```

Preserve existing imports and plugin resolution with an npm alias:

```bash
npm install karma-firefox-launcher@npm:@stackline/karma-firefox-launcher
```

## Usage and API reference

### karma-firefox-launcher



> Launcher for Mozilla Firefox.

## `karma-firefox-launcher` is deprecated and is not accepting new features or general bug fixes.

See [deprecation notice for `karma`](https://github.com/karma-runner/karma#karma-is-deprecated-and-is-not-accepting-new-features-or-general-bug-fixes).

[Web Test Runner](https://modern-web.dev/docs/test-runner/overview/),
[`jasmine-browser-runner`](https://github.com/jasmine/jasmine-browser-runner),
and [`playwright-test`](https://github.com/hugomrdias/playwright-test) provide
browser-based unit testing solutions which can be used as a direct alternative.

## Installation

The easiest way is to keep `karma-firefox-launcher` as a devDependency in your `package.json`.

You can simple do it by:

```bash
npm install @stackline/karma-firefox-launcher --save-dev
```

## Configuration

```js
// karma.conf.js
module.exports = function (config) {
  config.set({
    plugins: [require("@stackline/karma-firefox-launcher")],
    browsers: [
      "Firefox",
      "FirefoxDeveloper",
      "FirefoxAurora",
      "FirefoxNightly",
    ],
  });
};
```

You can pass list of browsers as a CLI argument too:

```bash
karma start --browsers Firefox,Chrome
```

To run Firefox in headless mode, append `Headless` to the version name, e.g. `FirefoxHeadless`, `FirefoxNightlyHeadless`.

### Environment variables

You can specify the location of the Firefox executable using the following
environment variables:

- `FIREFOX_BIN` (for browser `Firefox` or `FirefoxHeadless`)
- `FIREFOX_DEVELOPER_BIN` (for browser `FirefoxDeveloper` or
  `FirefoxDeveloperHeadless`)
- `FIREFOX_AURORA_BIN` (for browser `FirefoxAurora` or `FirefoxAuroraHeadless`)
- `FIREFOX_NIGHTLY_BIN` (for browser `FirefoxNightly` or
  `FirefoxNightlyHeadless`)

### Custom Firefox location

In addition to Environment variables you can specify location of the Firefox executable in a custom launcher:

```js
browsers: ['Firefox68', 'Firefox78'],

customLaunchers: {
    Firefox68: {
        base: 'Firefox',
        name: 'Firefox68',
        command: '<path to FF68>/firefox.exe'
    },
    Firefox78: {
        base: 'Firefox',
        name: 'Firefox78',
        command: '<path to FF78>/firefox.exe'
    }
}
```

### Custom Preferences

To configure preferences for the Firefox instance that is loaded, you can specify a custom launcher in your Karma
config with the preferences under the `prefs` key:

```js
browsers: ['FirefoxAutoAllowGUM'],

customLaunchers: {
    FirefoxAutoAllowGUM: {
        base: 'Firefox',
        prefs: {
            'media.navigator.permission.disabled': true
        }
    }
}
```

### Loading Firefox Extensions

If you have extensions that you want loaded into the browser on startup, you can specify the full path to each
extension in the `extensions` key:

```js
browsers: ['FirefoxWithMyExtension'],

customLaunchers: {
    FirefoxWithMyExtension: {
        base: 'Firefox',
        extensions: [
          path.resolve(__dirname, 'helpers/extensions/myCustomExt@suchandsuch.xpi'),
          path.resolve(__dirname, 'helpers/extensions/myOtherExt@soandso.xpi')
        ]
    }
}
```

**Please note**: the extension name must exactly match the 'id' of the extension. You can discover the 'id' of your
extension by extracting the .xpi (i.e. `unzip XXX.xpi`) and opening the install.RDF file with a text editor, then look
for the `em:id` tag under the `Description` tag. If your extension manifest looks something like this:

```xml
<?xml version="1.0" encoding="utf-8"?>
   <RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:em="http://www.mozilla.org/2004/em-rdf#">
  <Description about="urn:mozilla:install-manifest">
    <em:id>myCustomExt@suchandsuch</em:id>
    <em:version>1.0</em:version>
    <em:type>2</em:type>
    <em:bootstrap>true</em:bootstrap>
    <em:unpack>false</em:unpack>

    [...]
  </Description>
</RDF>
```

Then you should name your extension `myCustomExt@suchandsuch.xpi`.

---

For more information on Karma see the [homepage].

[homepage]: https://karma-runner.github.io

## Credits and original authors

- Original project: [karma-firefox-launcher](https://github.com/karma-runner/karma-firefox-launcher).
- Vojta Jina.
- Alex Zaslavsky.
- Andrei Khveras.
- Brian Birtles.
- Chad McElligott.
- dignifiedquire.
- Erwann Mest.
- Friedel Ziegelmayer.
- James Talmage.
- Jan Brecka.
- Jonathan Ginsburg.
- Liam Newman.
- Maksim Ryzhikov.
- Mario Vejlupek.
- Mark Ethan Trostler.
- Martin Fochler.
- Michał Gołębiowski.
- Parashuram.
- Peter Johanson.
- Salvador de la Puente.
- Schaaf, Martin.
- Žilvinas Urbonas.
- Copyright (C) 2011-2013 Google, Inc.
- Stackline maintenance: [Alexandro Paixao Marques](https://www.linkedin.com/in/aleinfo/) and [Stackline contributors](https://github.com/alexandroit).

Original copyright, license notices and contributor acknowledgements remain part of this distribution. Stackline maintenance does not replace authorship of the original work.

## License

`MIT`. See the license and notice files in the [repository](https://github.com/alexandroit/stackline-karma-firefox-launcher).

## Community and Links

- [Stackline website](https://alexandro.net/)
- [GitHub projects](https://github.com/alexandroit)
- [npm packages](https://www.npmjs.com/~alex360qc)
- [Reddit community — r/Stackline](https://www.reddit.com/r/Stackline/)
- [Maintainer LinkedIn](https://www.linkedin.com/in/aleinfo/)

Use this repository's issue tracker for reproducible bugs and feature requests. Join r/Stackline for examples, usage questions and release discussions.
