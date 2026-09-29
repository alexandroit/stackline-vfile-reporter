# @stackline/vfile-reporter

> vfile utility to create a report for a file.

[![npm version](https://img.shields.io/npm/v/@stackline/vfile-reporter.svg?style=flat-square)](https://www.npmjs.com/package/@stackline/vfile-reporter)
[![license](https://img.shields.io/npm/l/@stackline/vfile-reporter.svg?style=flat-square)](https://github.com/alexandroit/stackline-vfile-reporter)
[![GitHub repository](https://img.shields.io/badge/GitHub-alexandroit%2Fstackline-vfile-reporter-181717?style=flat-square&logo=github)](https://github.com/alexandroit/stackline-vfile-reporter)
[![Docs](https://img.shields.io/badge/docs-alexandro.net-0f766e?style=flat-square)](https://alexandro.net/docs/vanilla/vfile-reporter/)
[![Reddit community](https://img.shields.io/badge/community-r%2FStackline-ff4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/r/Stackline/)

**[Documentation](https://alexandro.net/docs/vanilla/vfile-reporter/)** | **[npm](https://www.npmjs.com/package/@stackline/vfile-reporter)** | **[Issues](https://github.com/alexandroit/stackline-vfile-reporter/issues)** | **[Repository](https://github.com/alexandroit/stackline-vfile-reporter)**

**Current package version:** `1.0.1`

---

## Why this package?

`@stackline/vfile-reporter` is the Stackline-maintained distribution of `vfile-reporter@7.0.5`. It is an independent continuation of [vfile-reporter](https://github.com/vfile/vfile-reporter); original authors and licenses remain credited below.

## Compatibility

| Item | Value |
| :--- | :--- |
| Package | `@stackline/vfile-reporter@1.0.1` |
| API target | `vfile-reporter@7.0.5` |
| Supported Node.js | `See supported framework requirements` |
| License | `MIT` |
| Module type | `module` |
| Main entry | `index.js` |
| Types | `index.d.ts` |
| Runtime dependencies | `vfile, vfile-sort, string-width, vfile-message, supports-color, vfile-statistics, @types/supports-color, unist-util-stringify-position` |

## Installation

```bash
npm install @stackline/vfile-reporter
```

Preserve existing imports and plugin resolution with an npm alias:

```bash
npm install vfile-reporter@npm:@stackline/vfile-reporter
```

## Usage and API reference

### vfile-reporter


[vfile][] utility to create a report.


## Contents

*   [What is this?](#what-is-this)
*   [When should I use this?](#when-should-i-use-this)
*   [Install](#install)
*   [Use](#use)
*   [API](#api)
    *   [`reporter(files[, options])`](#reporterfiles-options)
    *   [`Options`](#options)
*   [Types](#types)
*   [Compatibility](#compatibility)
*   [Security](#security)
*   [Related](#related)
*   [Contribute](#contribute)
*   [License](#license)

## What is this?

This package create a textual report from a file showing the warnings that
occurred while processing.
Many CLIs of tools that process files, whether linters (such as ESLint) or
bundlers (such as esbuild), have similar functionality.

## When should I use this?

You can use this package whenever you want to display a report about what
occurred while processing to a human.

There are [other reporters][reporters] that display information differently
listed in vfile.

## Install

This package is [ESM only][esm].
In Node.js (version 14.14+ and 16.0+), install with [npm][]:

```sh
npm install @stackline/vfile-reporter
```

In Deno with [`esm.sh`][esmsh]:

```js
import {reporter} from 'https://esm.sh/vfile-reporter@7'
```

In browsers with [`esm.sh`][esmsh]:

```html
<script type="module">
  import {reporter} from 'https://esm.sh/vfile-reporter@7?bundle'
</script>
```

## Use

Say our module `example.js` looks as follows:

```js
import {VFile} from 'vfile'
import {reporter} from '@stackline/vfile-reporter'

const one = new VFile({path: 'test/fixture/1.js'})
const two = new VFile({path: 'test/fixture/2.js'})

one.message('Warning!', {line: 2, column: 4})

console.error(reporter([one, two]))
```

…now running `node example.js` yields:

```txt
test/fixture/1.js
  2:4  warning  Warning!

test/fixture/2.js: no issues found

⚠ 1 warning
```

## API

This package exports the identifier [`reporter`][api-reporter].
That value is also the `default` export.

### `reporter(files[, options])`

Create a report from an error, one file, or multiple files.

###### Parameters

*   `files` ([`VFile`][vfile], `Array<VFile>`, or `Error`)
    — files or error to report
*   `options` ([`Options`][api-options], optional)
    — configuration

###### Returns

Report (`string`).

### `Options`

Configuration (TypeScript type).

###### Fields

*   `color` (`boolean`, default: depends)
    — use ANSI colors in report, the default behavior in Node.js is the check
    if [color is supported][supports-color]
*   `verbose` (`boolean`, default: `false`)
    — show message [`note`][message-note]s, notes are optional, additional,
    long descriptions
*   `quiet` (`boolean`, default: `false`)
    — do not show files without messages
*   `silent` (`boolean`, default: `false`)
    — show errors only, this hides info and warning messages, and sets
    `quiet: true`
*   `defaultName` (`string`, default: `'<stdin>'`).
    — label to use for files without file path, if one file and no
    `defaultName` is given, no name will show up in the report

## Types

This package is fully typed with [TypeScript][].
It exports the additional type [`Options`][api-options].

## Compatibility

Projects maintained by the unified collective are compatible with all maintained
versions of Node.js.
As of now, that is Node.js 14.14+ and 16.0+.
Our projects sometimes work with older versions, but this is not guaranteed.

## Security

Use of `vfile-reporter` is safe.

## Related

*   [`vfile-reporter-json`](https://github.com/vfile/vfile-reporter-json)
    — create a JSON report
*   [`vfile-reporter-pretty`](https://github.com/vfile/vfile-reporter-pretty)
    — create a pretty report
*   [`vfile-reporter-junit`](https://github.com/kellyselden/vfile-reporter-junit)
    — create a jUnit report
*   [`vfile-reporter-position`](https://github.com/Hocdoc/vfile-reporter-position)
    — create a report with content excerpts

## Contribute

See [`contributing.md`][contributing] in [`vfile/.github`][health] for ways to
get started.
See [`support.md`][support] for ways to get help.

This project has a [code of conduct][coc].
By interacting with this repository, organisation, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

Forked from [ESLint][]s stylish reporter
(originally created by Sindre Sorhus), which is Copyright (c) 2013
Nicholas C. Zakas, and licensed under MIT.



[build-badge]: https://github.com/vfile/vfile-reporter/workflows/main/badge.svg

[build]: https://github.com/vfile/vfile-reporter/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/vfile/vfile-reporter.svg

[coverage]: https://codecov.io/github/vfile/vfile-reporter

[downloads-badge]: https://img.shields.io/npm/dm/vfile-reporter.svg

[downloads]: https://www.npmjs.com/package/vfile-reporter

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/vfile/vfile/discussions

[npm]: https://docs.npmjs.com/cli/install

[esm]: https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c

[esmsh]: https://esm.sh

[typescript]: https://www.typescriptlang.org

[contributing]: https://github.com/vfile/.github/blob/main/contributing.md

[support]: https://github.com/vfile/.github/blob/main/support.md

[health]: https://github.com/vfile/.github

[coc]: https://github.com/vfile/.github/blob/main/code-of-conduct.md

[license]: license

[author]: https://wooorm.com

[eslint]: https://github.com/eslint/eslint

[vfile]: https://github.com/vfile/vfile

[reporters]: https://github.com/vfile/vfile#reporters

[supports-color]: https://github.com/chalk/supports-color

[message-note]: https://github.com/vfile/vfile-message#note

[screenshot]: screenshot.png

[api-reporter]: #reporterfiles-options

[api-options]: #options

## Credits and original authors

- Original project: [vfile-reporter](https://github.com/vfile/vfile-reporter).
- Titus Wormer.
- Copyright (c) 2015 Titus Wormer <tituswormer@gmail.com>.
- Copyright (c) 2013 Nicholas C. Zakas. All rights reserved.
- Stackline maintenance: [Alexandro Paixao Marques](https://www.linkedin.com/in/aleinfo/) and [Stackline contributors](https://github.com/alexandroit).

Original copyright, license notices and contributor acknowledgements remain part of this distribution. Stackline maintenance does not replace authorship of the original work.

## Community and Links

- [Stackline website](https://alexandro.net/)
- [GitHub projects](https://github.com/alexandroit)
- [npm packages](https://www.npmjs.com/~alex360qc)
- [Reddit community — r/Stackline](https://www.reddit.com/r/Stackline/)
- [Maintainer LinkedIn](https://www.linkedin.com/in/aleinfo/)

Use this repository's issue tracker for reproducible bugs and feature requests. Join r/Stackline for examples, usage questions and release discussions.
