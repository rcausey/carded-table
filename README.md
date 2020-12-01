# d2l-labs-carded-table

[![NPM version](https://img.shields.io/npm/v/@brightspace-ui-labs/carded-table.svg)](https://www.npmjs.org/package/@brightspace-ui-labs/carded-table)

> Note: this is a ["labs" component](https://github.com/BrightspaceUI/guide/wiki/Component-Tiers). While functional, these tasks are prerequisites to promotion to BrightspaceUI "official" status:
>
> - [ ] [Design organization buy-in](https://github.com/BrightspaceUI/guide/wiki/Before-you-build#working-with-design)
> - [ ] [design.d2l entry](http://design.d2l/)
> - [ ] [Architectural sign-off](https://github.com/BrightspaceUI/guide/wiki/Before-you-build#web-component-architecture)
> - [x] [Continuous integration](https://github.com/BrightspaceUI/guide/wiki/Testing#testing-continuously-with-travis-ci)
> - [x] [Cross-browser testing](https://github.com/BrightspaceUI/guide/wiki/Testing#cross-browser-testing-with-sauce-labs)
> - [x] [Unit tests](https://github.com/BrightspaceUI/guide/wiki/Testing#testing-with-polymer-test)
> - [x] [Accessibility tests](https://github.com/BrightspaceUI/guide/wiki/Testing#automated-accessibility-testing-with-axe)
> - [ ] [Visual diff tests](https://github.com/BrightspaceUI/visual-diff)
> - [x] [Localization](https://github.com/BrightspaceUI/guide/wiki/Localization) with Serge (N/A)
> - [x] Demo page
> - [x] README documentation

Carded table component for displaying content as rows of cards. "Cells" in the table are aligned to the column headers.

## Installation

To install from NPM:

```shell
npm install @brightspace-ui-labs/carded-table
```

## Usage

```html
<script type="module">
	import '@brightspace-ui-labs/carded-table/carded-table-card.js';
	import '@brightspace-ui-labs/carded-table/carded-table-cards.js';
	import '@brightspace-ui-labs/carded-table/carded-table-header.js';
	import '@brightspace-ui-labs/carded-table/carded-table-heading.js';
	import '@brightspace-ui-labs/carded-table/carded-table.js';
</script>

<d2l-labs-carded-table default-columns>
	<d2l-labs-carded-table-header>
		<d2l-labs-carded-table-heading>Column 1</d2l-labs-carded-table-heading>
		<d2l-labs-carded-table-heading>Column 2</d2l-labs-carded-table-heading>
	</d2l-labs-carded-table-header>
	<d2l-labs-carded-table-cards>
		<d2l-labs-carded-table-card>
			<div>Card 1 Element 1</div>
			<div>Card 1 Element 2</div>
		</d2l-labs-carded-table-card>
		<d2l-labs-carded-table-card>
			<div>Card 2 Element 1</div>
			<div>Card 2 Element 2</div>
		</d2l-labs-carded-table-card>
	</d2l-labs-carded-table-cards>
</d2l-labs-carded-table>
```


 ## Properties & Info

 ### `d2l-labs-carded-table`
- `default-columns`: Automatically adds `grid-template-column` to the header and card elements, based on the number of headings. Defaults to `1fr` width for each column.
  - e.g., in the demo above,  `grid-template-columns: repeat(2, 1fr)` would be added.

 - For custom column sizes, add your own `grid-template-column` to both the `d2l-labs-carded-table-header` and `d2l-labs-carded-table-card` elements.
  - (See `demo/carded-table-course-demo.js` for an example)

 ### `d2l-labs-carded-table-header`
- Wrapper for headings - apply the `grid-template-columns` on this element to line up content in the cards.

 ### `d2l-labs-carded-table-heading`
- This contains the content of the heading.

 ### `d2l-labs-carded-table-card`
- This contains the content that appears in the cards. The number of 'cells' should line up with the number of columns specified.


## Developing, Testing and Contributing

After cloning the repo, run `npm install` to install dependencies.

If you don't have it already, install the [Polymer CLI](https://www.polymer-project.org/3.0/docs/tools/polymer-cli) globally:

```shell
npm install -g polymer-cli
```

### Running the demos

To start a [local web server](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#serve) that hosts the demo page and tests:

```shell
polymer serve
```

### Testing

To lint ([eslint](http://eslint.org/) and [Polymer lint](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#lint)):

```shell
npm run lint
```

To run unit tests locally using [Polymer test](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#tests):

```shell
npm run test:polymer:local
```

To lint AND run local unit tests:

```shell
npm test
```

[ci-url]: https://travis-ci.org/BrightspaceUILabs/carded-table
[ci-image]: https://travis-ci.org/BrightspaceUILabs/carded-table.svg?branch=master

### Running the demos

To start a [local web server](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#serve) that hosts the demo page and tests:

```shell
polymer serve
```

### Testing

To lint:

```shell
npm run lint
```

To run local unit tests:

```shell
npm run test:local
```

To run a subset of local unit tests, modify your local [index.html](https://github.com/BrightspaceUILabs/carded-table/blob/master/test/index.html), or start the dev server and navigate to the desired test page.

To run linting and unit tests:

```shell
npm test
```

## Versioning & Releasing

> TL;DR: Commits prefixed with `fix:` and `feat:` will trigger patch and minor releases when merged to `master`. Read on for more details...

The [sematic-release GitHub Action](https://github.com/BrightspaceUI/actions/tree/master/semantic-release) is called from the `release.yml` GitHub Action workflow to handle version changes and releasing.

### Version Changes

All version changes should obey [semantic versioning](https://semver.org/) rules:
1. **MAJOR** version when you make incompatible API changes,
2. **MINOR** version when you add functionality in a backwards compatible manner, and
3. **PATCH** version when you make backwards compatible bug fixes.

The next version number will be determined from the commit messages since the previous release. Our semantic-release configuration uses the [Angular convention](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-angular) when analyzing commits:
* Commits which are prefixed with `fix:` or `perf:` will trigger a `patch` release. Example: `fix: validate input before using`
* Commits which are prefixed with `feat:` will trigger a `minor` release. Example: `feat: add toggle() method`
* To trigger a MAJOR release, include `BREAKING CHANGE:` with a space or two newlines in the footer of the commit message
* Other suggested prefixes which will **NOT** trigger a release: `build:`, `ci:`, `docs:`, `style:`, `refactor:` and `test:`. Example: `docs: adding README for new component`

To revert a change, add the `revert:` prefix to the original commit message. This will cause the reverted change to be omitted from the release notes. Example: `revert: fix: validate input before using`.

### Releases

When a release is triggered, it will:
* Update the version in `package.json`
* Tag the commit
* Create a GitHub release (including release notes)
* Deploy a new package to NPM

### Releasing from Maintenance Branches

Occasionally you'll want to backport a feature or bug fix to an older release. `semantic-release` refers to these as [maintenance branches](https://semantic-release.gitbook.io/semantic-release/usage/workflow-configuration#maintenance-branches).

Maintenance branch names should be of the form: `+([0-9])?(.{+([0-9]),x}).x`.

Regular expressions are complicated, but this essentially means branch names should look like:
* `1.15.x` for patch releases on top of the `1.15` release (after version `1.16` exists)
* `2.x` for feature releases on top of the `2` release (after version `3` exists)
