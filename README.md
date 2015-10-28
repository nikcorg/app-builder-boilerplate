# App builder boilerplate

After rewriting this boilerplate build and watch scripts over and over again, I've finally compiled it into a cloneable repo.

Original inspiration from [Task Automation with Npm Run](http://substack.net/task_automation_with_npm_run). Lots of improvements and further inspiration from [How to Use npm as a Build Tool](http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/).

## Getting started

Run `npm install` to fetch dependencies and to install git hooks. Git hooks are used for linting and running tests before pushing and merging.

## Developing and Building

- `npm run watch` builds with `NODE_ENV=dev`. Watches files in `/src`. Rebuilds on every change.
- `npm run build` makes a build with `NODE_ENV=production`.
- `npm run test` runs all in `/src` which matches `*.spec.js` using [tape](https://npmjs.com/package/tape).

Files are built with a version suffix into `/pub/`, e.g. `pub/bundle-1.0.0.js`.

An app cache manifest file is also built. All files in `/pub` will be included in the files list.

## Bundled Deps

- [debug](https://npmjs.com/package/debug)

## Tools Used in the Build

All watch tasks make use of:

- [parallelshell](https://npmjs.com/package/parallelshell)
- [nodemon](https://npmjs.com/package/nodemon)

### CSS

- [postcss](https://npmjs.com/package/postcss)
    - [cssnext](https://npmjs.com/package/cssnext)

### JavaScript

- [browserify](https://npmjs.com/package/browserify)
    - [babelify](https://npmjs.com/package/babelify)
    - [envify](https://npmjs.com/package/envify)

### HTML and AppCache Manifest

The strings `__VERSION__` and `__MANIFEST__` in the source are replaced with the version number and manifest file name from `package.json` respectively.

`find` and `sed` are used to compile the HTML and AppCache manifest.
