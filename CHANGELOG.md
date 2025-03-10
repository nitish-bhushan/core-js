## Changelog
##### Unreleased
- Fixed detection of forbidden host code points in URL polyfill
- Allowed `rhino` target in `core-js-compat` / `core-js-builder`, added compat data for `rhino` 1.7.13, [#942](https://github.com/zloirock/core-js/issues/942), thanks [@gausie](https://github.com/gausie)
- `.at` marked as supported from FF90

##### 3.14.0 - 2021.06.05
- Added polyfill of stable sort in `{ Array, %TypedArray% }.prototype.sort`, [#769](https://github.com/zloirock/core-js/issues/769), [#941](https://github.com/zloirock/core-js/issues/941)
- Fixed `Safari` 14.0- `%TypedArray%.prototype.sort` validation of arguments bug
- `.at` marked as supported from V8 9.2

##### 3.13.1 - 2021.05.29
- Overwrites `get-own-property-symbols` third-party `Symbol` polyfill if it's used since it causes a stack overflow, [#774](https://github.com/zloirock/core-js/issues/774)
- Added a workaround of possible browser crash on `Object.prototype` accessors methods in WebKit ~ Android 4.0, [#232](https://github.com/zloirock/core-js/issues/232)

##### 3.13.0 - 2021.05.26
- Accessible `Object#hasOwnProperty` (`Object.hasOwn`) proposal moved to the stage 3, [May 2021 TC39 meeting](https://github.com/babel/proposals/issues/74#issuecomment-848121673)

##### 3.12.1 - 2021.05.09
- Fixed some cases of `Function#toString` with multiple `core-js` instances
- Fixed some possible `String#split` polyfill problems in V8 5.1

##### 3.12.0 - 2021.05.06
- Added well-known symbol `Symbol.metadata` for [decorators stage 2 proposal](https://github.com/tc39/proposal-decorators)
- Added well-known symbol `Symbol.matcher` for [pattern matching stage 1 proposal](https://github.com/tc39/proposal-pattern-matching)
- Fixed regression of V8 ~ Node 0.12 `String(Symbol())` bug, [#933](https://github.com/zloirock/core-js/issues/933)  

##### 3.11.3 - 2021.05.05
- Native promise-based APIs `Promise#{ catch, finally }` returns polyfilled `Promise` instances when it's required

##### 3.11.2 - 2021.05.03
- Added a workaround of WebKit ~ iOS 10.3 Safari `Promise` bug, [#932](https://github.com/zloirock/core-js/issues/932)
- `Promise#then` of incorrect native `Promise` implementations with correct subclassing no longer wrapped
- Changed the order of `Promise` feature detection, removed unhandled rejection tracking check in non-browser non-node platforms

##### 3.11.1 - 2021.04.28
- Made `instanceof Promise` and `.constructor === Promise` work with polyfilled `Promise` for all native promise-based APIs
- Added a workaround for some buggy V8 versions \~4.5 related to fixing of `%TypedArray%` static methods, [#564](https://github.com/zloirock/core-js/issues/564)

##### 3.11.0 - 2021.04.22
- Added [accessible `Object#hasOwnProperty` stage 2 proposal](https://github.com/tc39/proposal-accessible-object-hasownproperty)
  - `Object.hasOwn` method
- Fixed a possible `RegExp` constructor problem with multiple global `core-js` instances

##### 3.10.2 - 2021.04.19
- `URL` and `URLSearchParams` marked as supported from Safari 14.0
- Polyfilled built-in constructors protected from calling on instances

##### 3.10.1 - 2021.04.08
- Prevented possible `RegExp#split` problems in old engines, [#751](https://github.com/zloirock/core-js/issues/751), [#919](https://github.com/zloirock/core-js/issues/919)
- Detection of Safari 10 string padding bug extended to some Safari-based browsers

##### 3.10.0 - 2021.03.31
- [`Array` find from last proposal](https://github.com/tc39/proposal-array-find-from-last) moved to the stage 2, [March TC39 meeting](https://github.com/babel/proposals/issues/71#issuecomment-795916535)
- Prevented possible `RegExp#exec` problems in some old engines, [#920](https://github.com/zloirock/core-js/issues/920)
- Updated compat data mapping:
  - NodeJS up to 16.0
  - Electron up to 13.0
  - Samsung Internet up to 14.0
  - Opera Android up to 62
  - The rest automatically

##### 3.9.1 - 2021.03.01
- Added a workaround for Chrome 38-40 bug which does not allow to inherit symbols (incl. well-known) from DOM collections prototypes to instances, [#37](https://github.com/zloirock/core-js/issues/37)
- Used `NumericRangeIterator` as toStringTag instead of `RangeIterator` in `{ Number, BigInt }.range` iterator, per [this PR](https://github.com/tc39/proposal-Number.range/pull/46)
- TypedArray constructors marked as supported from Safari 14.0
- Updated compat data mapping for iOS Safari and Opera for Android

##### 3.9.0 - 2021.02.19
- Added [`Array` find from last stage 1 proposal](https://github.com/tc39/proposal-array-find-from-last)
  - `Array#findLast`
  - `Array#findLastIndex`
  - `%TypedArray%#findLast`
  - `%TypedArray%#findLastIndex`
- Added `%TypedArray%#uniqueBy` method for [array deduplication stage 1 proposal](https://github.com/tc39/proposal-array-unique)
  - `%TypedArray%#uniqueBy`
- Dropped `ToLength` detection from array methods feature detection which could cause hanging FF11-21 and some versions of old WebKit, [#764](https://github.com/zloirock/core-js/issues/764)
- Minified bundle from `core-js-bundle` uses `terser` instead of `uglify-js`

##### 3.8.3 - 2021.01.19
- Fixed some more issues related to FF44- legacy `Iterator`, [#906](https://github.com/zloirock/core-js/issues/906)

##### 3.8.2 - 2021.01.03
- Fixed handling of special replacements patterns in `String#replaceAll`, [#900](https://github.com/zloirock/core-js/issues/900)
- Fixed iterators dependencies of `Promise.any` and `Promise.allSettled` entries
- Fixed microtask implementation on WebOS, [#898](https://github.com/zloirock/core-js/issues/898), [#901](https://github.com/zloirock/core-js/issues/901)

##### 3.8.1 - 2020.12.06
- Fixed work of new `%TypedArray%` methods on `BigInt` arrays
- Added ESNext methods to ES3 workaround for `Number` constructor wrapper

##### 3.8.0 - 2020.11.26
- Added [relative indexing method stage 3 proposal](https://github.com/tc39/proposal-relative-indexing-method)
  - `Array#at`
  - `%TypedArray%#at`
- Added [`Number.range` stage 1 proposal](https://github.com/tc39/proposal-Number.range)
  - `Number.range`
  - `BigInt.range`
- Added [array filtering stage 1 proposal](https://github.com/tc39/proposal-array-filtering)
  - `Array#filterOut`
  - `%TypedArray%#filterOut`
- Added [array deduplication stage 1 proposal](https://github.com/tc39/proposal-array-unique)
  - `Array#uniqueBy`
- Added code points / code units explicit feature detection in `String#at` for preventing breakage code which use obsolete `String#at` proposal polyfill
- Added the missed `(es|stable)/instance/replace-all` entries
- Updated compat data mapping for Opera - from Opera 69, the difference with Chrome versions increased to 14
- Compat data mapping for modern Android WebView to Chrome moved from targets parser directly to compat data
- Depracate `core-js-builder` `blacklist` option in favor of `exclude`

##### 2.6.12 [LEGACY] - 2020.11.26
- Added code points / code units explicit feature detection in `String#at` for preventing breakage code which use obsolete `String#at` proposal polyfill
- Added `OPEN_SOURCE_CONTRIBUTOR` detection in `postinstall`
- Added Drone CI detection in `postinstall`

##### 3.7.0 - 2020.11.06
- `String#replaceAll` moved to the stable ES, [per June TC39 meeting](https://github.com/tc39/notes/blob/master/meetings/2020-06/june-2.md#stringprototypereplaceall-for-stage-4)
- `Promise.any` and `AggregateError` moved to the stable ES, [per July TC39 meeting](https://github.com/tc39/notes/blob/master/meetings/2020-07/july-21.md#promiseany--aggregateerror-for-stage-4)
- Added `Reflect[@@toStringTag]`, [per July TC39 meeting](https://github.com/tc39/ecma262/pull/2057)
- Forced replacement of `Array#{ reduce, reduceRight }` in Chrome 80-82 because of [a bug](https://bugs.chromium.org/p/chromium/issues/detail?id=1049982), [#766](https://github.com/zloirock/core-js/issues/766)
- Following the changes in [the `upsert` proposal](https://github.com/tc39/proposal-upsert), `{ Map, WeakMap }#emplace` replace `{ Map, WeakMap }#upsert`, these obsolete methods will be removed in the next major release
- [By the current spec](https://tc39.es/ecma262/#sec-aggregate-error-constructor), `AggregateError#errors` is own data property
- Added correct iteration closing in the iteration helpers according to the current version of [the proposal](https://tc39.es/proposal-iterator-helpers)
- `process.nextTick` have a less priority than `Promise` in the microtask implementation, [#855](https://github.com/zloirock/core-js/issues/855)
- Fixed microtask implementation in engines with `MutationObserver`, but without `document`, [#865](https://github.com/zloirock/core-js/issues/865), [#866](https://github.com/zloirock/core-js/issues/866)
- Fixed `core-js-builder` with an empty (after the targets engines or another filtration) modules list, [#822](https://github.com/zloirock/core-js/issues/822)
- Fixed possible twice call of `window.onunhandledrejection`, [#760](https://github.com/zloirock/core-js/issues/760)
- Fixed some possible problems related multiple global copies of `core-js`, [#880](https://github.com/zloirock/core-js/issues/880)
- Added a workaround for 3rd party `Reflect.set` polyfill bug, [#847](https://github.com/zloirock/core-js/issues/847)
- Updated compat data:
  - Chrome up to 86
  - FF up to 82
  - Safari up to 14
- Updated compat data mapping:
  - iOS up to 14
  - NodeJS up to 15.0
  - Electron up to 11.0
  - Samsung Internet up to 13.0
  - Opera Android up to 60
  - The rest automatically
- Updated all required dependencies

##### 3.6.5 - 2020.04.09
- Updated Browserlist [#755](https://github.com/zloirock/core-js/issues/755)
- Fixed `setImmediate` in Safari [#770](https://github.com/zloirock/core-js/issues/770), thanks [@dtinth](https://github.com/dtinth)
- Fixed some regexp, thanks [@scottarc](https://github.com/scottarc)
- Added OPEN_SOURCE_CONTRIBUTOR detection in `postinstall`, thanks [@scottarc](https://github.com/scottarc)
- Added Drone CI in `postinstall` CI detection [#781](https://github.com/zloirock/core-js/issues/781)

##### 3.6.4 - 2020.01.14
- Prevented a possible almost infinite loop in non-standard implementations of some backward iteration array methods

##### 3.6.3 - 2020.01.11
- Fixed replacement of substitutes of undefined capture groups in `.replace` in Safari 13.0-, [#471](https://github.com/zloirock/core-js/issues/471), [#745](https://github.com/zloirock/core-js/issues/745), thanks [@mattclough1](https://github.com/mattclough1)
- Improved compat data for old engines

##### 3.6.2 - 2020.01.07
- Fixed early implementations of `Array#{ every, forEach, includes, indexOf, lastIndexOf, reduce, reduceRight, slice, some, splice }` for the usage of `ToLength`
- Added `RegExp#exec` dependency to methods which depends on the correctness of logic of this method (`3.6.0-3.6.1` issue), [#741](https://github.com/zloirock/core-js/issues/741)
- Refactored some internals

##### 3.6.1 - 2019.12.25
- Fixed a bug related `Symbol` with multiple copies of `core-js` (for `3.4.2-3.6.0`), [#736](https://github.com/zloirock/core-js/issues/736)
- Refactored some tools

##### 3.6.0 - 2019.12.19
- Added support of sticky (`y`) `RegExp` flag, [#372](https://github.com/zloirock/core-js/issues/372), [#732](https://github.com/zloirock/core-js/issues/732), [#492](https://github.com/zloirock/core-js/issues/492), thanks [@cvle](https://github.com/cvle) and [@nicolo-ribaudo](https://github.com/nicolo-ribaudo)
- Added `RegExp#test` delegation to `RegExp#exec`, [#732](https://github.com/zloirock/core-js/issues/732), thanks [@cvle](https://github.com/cvle)
- Fixed some cases of `Object.create(null)` in IE8-, [#727](https://github.com/zloirock/core-js/issues/727), [#728](https://github.com/zloirock/core-js/issues/728), thanks [@aleen42](https://github.com/aleen42)
- Allowed object of minimum environment versions as `core-js-compat` and `core-js-builder` `targets` argument
- Allowed corresponding to Babel `targets.esmodules`, `targets.browsers`, `targets.node` options in `core-js-compat` and `core-js-builder`
- Engines in compat data and results of targets parsing sorted alphabetically
- Fixed `features/instance/match-all` entry compat data
- Fixed `Array.prototype[@@unscopables]` descriptor (was writable)
- Added Samsung Internet 11 compat data mapping

##### 3.5.0 - 2019.12.12
- Added [object iteratoration stage 1 proposal](https://github.com/tc39/proposal-object-iteration):
  - `Object.iterateKeys`
  - `Object.iterateValues`
  - `Object.iterateEntries`

##### 3.4.8 - 2019.12.09
- Added one more workaround for broken in previous versions `inspectSource` helper, [#719](https://github.com/zloirock/core-js/issues/719)
- Added Opera Mobile compat data
- Updated Samsung Internet, iOS, old Node and Android compat data mapping
- `es.string.match-all` marked as completely supported in FF73
- Generate `core-js-compat/modules` since often we need just the list of `core-js` modules

##### 2.6.11 [LEGACY] - 2019.12.09
- Returned usage of `node -e` in the `postinstall` scripts for better cross-platform compatibility, [#582](https://github.com/zloirock/core-js/issues/582)
- Improved CI detection in the `postinstall` script, [#707](https://github.com/zloirock/core-js/issues/707)

##### 3.4.7 - 2019.12.03
- Fixed an NPM publishing issue

##### 3.4.6 - 2019.12.03
- Improved iOS compat data - added missed mapping iOS 12.2 -> Safari 12.1, added bug fixes from patch releases
- Added Safari 13.1 compat data
- Added missed in `core-js-compat` helpers `ie_mob` normalization
- Normalize the result of `getModulesListForTargetVersion` `core-js-compat` helper
- Improved CI detection in the `postinstall` script, [#707](https://github.com/zloirock/core-js/issues/707)

##### 3.4.5 - 2019.11.28
- Detect incorrect order of operations in `Object.assign`, MS Edge bug
- Detect usage of `ToLength` in `Array#{ filter, map }`, FF48-49 and MS Edge 14- issues
- Detect incorrect MS Edge 17-18 `Reflect.set` which allows setting the property to object with non-writable property on the prototype
- Fixed `inspectSource` helper with multiple `core-js` copies and some related features like some edge cases of `Promise` feature detection

##### 3.4.4 - 2019.11.27
- Added feature detection for Safari [non-generic `Promise#finally` bug](https://bugs.webkit.org/show_bug.cgi?id=200829) **(critical for `core-js-pure`)**
- Fixed missed `esnext.string.code-points` in `core-js/features/string` entry point
- Updated `Iterator` proposal feature detection for the case of non-standard `Iterator` in FF44-

##### 3.4.3 - 2019.11.26
- Fixed missed `es.json.stringify` and some modules from iteration helpers proposal in some entry points **(includes the root entry point)**
- Added a workaround of `String#{ endsWith, startsWith }` MDN polyfills bugs, [#702](https://github.com/zloirock/core-js/issues/702)
- Fixed `.size` property descriptor of `Map` / `Set` in the pure version
- Refactoring, some internal improvements

##### 3.4.2 - 2019.11.22
- Don't use polyfilled symbols as internal uids, a workaround for some incorrect use cases
- `String#replaceAll` is available only in nightly FF builds
- Improved `Promise` feature detection for the case of V8 6.6 with multiple `core-js` copies
- Some internals optimizations
- Added Node 13.2 -> V8 7.9 compat data mapping
- Returned usage of `node -e` in `postinstall` scripts

##### 3.4.1 - 2019.11.12
- Throw when `(Async)Iterator#flatMap` mapper returns a non-iterable, per [tc39/proposal-iterator-helpers/55](https://github.com/tc39/proposal-iterator-helpers/issues/55) and [tc39/proposal-iterator-helpers/59](https://github.com/tc39/proposal-iterator-helpers/pull/59)
- Removed own `AggregateError#toString`, per [tc39/proposal-promise-any/49](https://github.com/tc39/proposal-promise-any/pull/49)
- Global `core-js` `Promise` polyfill passes feature detection in the pure versions
- Fixed indexes in `String#replaceAll` callbacks
- `String#replaceAll` marked as supported by FF72

##### 3.4.0 - 2019.11.07
- Added [well-formed `JSON.stringify`](https://github.com/tc39/proposal-well-formed-stringify), ES2019 feature, thanks [@ExE-Boss](https://github.com/ExE-Boss) and [@WebReflection](https://github.com/WebReflection) for the idea
- Fixed `Math.signbit`, [#687](https://github.com/zloirock/core-js/issues/687), thanks [@chicoxyzzy](https://github.com/chicoxyzzy)

##### 3.3.6 - 2019.11.01
- Don't detect Chakra-based Edge as Chrome in the `userAgent` parsing
- Fixed inheritance in typed array constructors wrappers, [#683](https://github.com/zloirock/core-js/issues/683)
- Added one more workaround for correct work of early `fetch` implementations with polyfilled `URLSearchParams`, [#680](https://github.com/zloirock/core-js/issues/680)

##### 3.3.5 - 2019.10.29
- Added a workaround of V8 deoptimization which causes serious performance degradation (~4x in my tests) of `Array#concat`, [#679](https://github.com/zloirock/core-js/issues/679)
- Added a workaround of V8 deoptimization which causes slightly performance degradation of `Promise`, [#679](https://github.com/zloirock/core-js/issues/679)
- Added `(Async)Iterator.prototype.constructor -> (Async)Iterator` per [this issue](https://github.com/tc39/proposal-iterator-helpers/issues/60)
- Added compat data for Chromium-based Edge

##### 3.3.4 - 2019.10.25
- Added a workaround of V8 deoptimization which causes serious performance degradation (~20x in my tests) of some `RegExp`-related methods like `String#split`, [#306](https://github.com/zloirock/core-js/issues/306)
- Added a workaround of V8 deoptimization which causes serious performance degradation (up to 100x in my tests) of `Array#splice` and slightly `Array#{ filter, map }`, [#677](https://github.com/zloirock/core-js/issues/677)
- Fixed work of `fetch` with polyfilled `URLSearchParams`, [#674](https://github.com/zloirock/core-js/issues/674)
- Fixed an edge case of `String#replaceAll` with an empty search value
- Added compat data for Chrome 80
- `package-lock.json` no longer generated in libraries

##### 3.3.3 - 2019.10.22
- `gopher` removed from `URL` special cases per [this issue](https://github.com/whatwg/url/issues/342) and [this PR](https://github.com/whatwg/url/pull/453)
- Added compat data for iOS 13 and Node 13.0

##### 3.3.2 - 2019.10.14
- Fixed compatibility of `core-js-compat` with Node 6 and Yarn, [#669](https://github.com/zloirock/core-js/issues/669) 

##### 3.3.1 - 2019.10.13
- Fixed an NPM publishing issue

##### 3.3.0 - 2019.10.13
- **`String#{ matchAll, replaceAll }` throws an error on non-global regex argument per [the decision from TC39 meetings](https://github.com/tc39/ecma262/pull/1716) (+ [this PR](https://github.com/tc39/proposal-string-replaceall/pull/24)). It's a breaking change, but since it's a breaking change in the ES spec, it's added at the minor release**
- `globalThis` moved to stable ES, [per October TC39 meeting](https://github.com/babel/proposals/issues/60#issuecomment-537217903)
- `Promise.any` moved to stage 3, some minor internal changes, [per October TC39 meeting](https://github.com/babel/proposals/issues/60#issuecomment-538084885)
- `String#replaceAll` moved to stage 3, [per October TC39 meeting](https://github.com/babel/proposals/issues/60#issuecomment-537530013)
- Added [iterator helpers stage 2 proposal](https://github.com/tc39/proposal-iterator-helpers):
  - `Iterator`
    - `Iterator.from`
    - `Iterator#asIndexedPairs`
    - `Iterator#drop`
    - `Iterator#every`
    - `Iterator#filter`
    - `Iterator#find`
    - `Iterator#flatMap`
    - `Iterator#forEach`
    - `Iterator#map`
    - `Iterator#reduce`
    - `Iterator#some`
    - `Iterator#take`
    - `Iterator#toArray`
    - `Iterator#@@toStringTag`
  - `AsyncIterator`
    - `AsyncIterator.from`
    - `AsyncIterator#asIndexedPairs`
    - `AsyncIterator#drop`
    - `AsyncIterator#every`
    - `AsyncIterator#filter`
    - `AsyncIterator#find`
    - `AsyncIterator#flatMap`
    - `AsyncIterator#forEach`
    - `AsyncIterator#map`
    - `AsyncIterator#reduce`
    - `AsyncIterator#some`
    - `AsyncIterator#take`
    - `AsyncIterator#toArray`
    - `AsyncIterator#@@toStringTag`
- Updated `Map#upsert` (`Map#updateOrInsert` before) [proposal](https://github.com/thumbsupep/proposal-upsert)
  - Moved to stage 2, [per October TC39 meeting](https://github.com/babel/proposals/issues/60#issuecomment-537606117)
  - `Map#updateOrInsert` renamed to `Map#upsert`
  - Added `WeakMap#upsert`
  - You can don't pass one of the callbacks
- Added a workaround for iOS Safari MessageChannel + bfcache bug, [#624](https://github.com/zloirock/core-js/issues/624)
- Added a workaround for Chrome 33 / Android 4.4.4 `Promise` bug, [#640](https://github.com/zloirock/core-js/issues/640)
- Replaced broken `URL` constructor in Safari and `URLSearchParams` in Chrome 66-, [#656](https://github.com/zloirock/core-js/issues/656)
- Added compat data for Node up to 12.11, FF 69, Samsung up to 10.2 and Phantom 1.9
- `Math.hypot` marked as not supported in Chrome 77 since [a bug in this method](https://bugs.chromium.org/p/v8/issues/detail?id=9546) was not fixed before the stable Chrome 77 release
- Fixed unnecessary exposing on `Symbol.matchAll` in `esnext.string.match-all`, [#626](https://github.com/zloirock/core-js/issues/626)
- Fixed missed cases [access the `.next` method once, at the beginning, of the iteration protocol](https://github.com/tc39/ecma262/issues/976)
- Show similar `postinstall` messages only once per `npm i`, [#597](https://github.com/zloirock/core-js/issues/597), thanks [@remy](https://github.com/remy)

##### 2.6.10 [LEGACY] - 2019.10.13
- Show similar `postinstall` messages only once per `npm i`, [#597](https://github.com/zloirock/core-js/issues/597)

##### 3.2.1 - 2019.08.12
- Added a workaround for possible recursion in microtasks caused by conflicts with other `Promise` polyfills, [#615](https://github.com/zloirock/core-js/issues/615)

##### 3.2.0 - 2019.08.09
- `Promise.allSettled` moved to stable ES, per July TC39 meeting
- `Promise.any` moved to stage 2, `.errors` property of `AggregateError` instances maked non-enumerable, per July TC39 meeting
- `using` statement proposal moved to stage 2, added `Symbol.asyncDispose`, per July TC39 meeting
- Added `Array.isTemplateObject` [stage 2 proposal](https://github.com/tc39/proposal-array-is-template-object), per June TC39 meeting
- Added `Map#updateOrInsert` [stage 1 proposal](https://docs.google.com/presentation/d/1_xtrGSoN1-l2Q74eCXPHBbbrBHsVyqArWN0ebnW-pVQ/), per July TC39 meeting
- Added a fix for [`Math.hypot` V8 7.7 bug](https://bugs.chromium.org/p/v8/issues/detail?id=9546), since it's still not stable without adding results to `core-js-compat`
- Added a workaround for APIs where not possible to replace broken native `Promise`, [#579](https://github.com/zloirock/core-js/issues/579) - added `.finally` and patched `.then` to / on native `Promise` prototype
- Fixed crashing of Opera Presto, [#595](https://github.com/zloirock/core-js/issues/595)
- Fixed incorrect early breaking of `{ Map, Set, WeakMap, WeakSet }.deleteAll`
- Fixed some missed dependencies in entry points
- Added compat data for Node 12.5, FF 67, Safari 13
- Added support of `DISABLE_OPENCOLLECTIVE` env variable to `postinstall` script
- Removed `core-js-pure` dependency from `core-js-compat`, [#590](https://github.com/zloirock/core-js/issues/590)
- Fixed generation of `core-js-compat` on Windows, [#606](https://github.com/zloirock/core-js/issues/606)

##### 3.1.4 - 2019.06.15
- Refactoring. Many minor internal improvements and fixes like:
  - Improved `Symbol.keyFor` complexity to `O(1)`
  - Fixed the order of arguments validation in `String.prototype.{ endsWith, includes, startsWith }`
  - Internal implementation of `RegExp#flags` helper now respect `dotAll` flag (mainly ralated to the `pure` version)
  - Performace optimizations related old V8
  - Etc.

##### 3.1.3 - 2019.05.27
- Fixed `core-js/features/reflect/delete-metadata` entry point
- Some fixes and improvements of the `postinstall` script like support `npm` color config ([#556](https://github.com/zloirock/core-js/issues/556)) or adding support of `ADBLOCK` env variable
- Refactoring and some minor fixes

##### 2.6.9 [LEGACY] - 2019.05.27
- Some fixes and improvements of the `postinstall` script like support `npm` color config ([#556](https://github.com/zloirock/core-js/issues/556)) or adding support of `ADBLOCK` env variable

##### 3.1.2 - 2019.05.22
- Added a workaround of a strange `npx` bug on `postinstall`, [#551](https://github.com/zloirock/core-js/issues/551)

##### 2.6.8 [LEGACY] - 2019.05.22
- Added a workaround of a strange `npx` bug on `postinstall`, [#551](https://github.com/zloirock/core-js/issues/551)

##### 3.1.1 - 2019.05.21
- Added one more workaround of alternative not completely correct `Symbol` polyfills, [#550](https://github.com/zloirock/core-js/issues/550), [#554](https://github.com/zloirock/core-js/issues/554)
- Reverted `esnext.string.match-all` in some entry points for fix autogeneration of `core-js-compat/entries` and backward `@babel/preset-env` compatibility

##### 2.6.7 [LEGACY] - 2019.05.21
- Added one more workaround of alternative not completely correct `Symbol` polyfills, [#550](https://github.com/zloirock/core-js/issues/550), [#554](https://github.com/zloirock/core-js/issues/554)

##### 3.1.0 - 2019.05.20
- `String#matchAll` moved to stable ES, exposed `Symbol.matchAll`, [#516](https://github.com/zloirock/core-js/issues/516)
- `Promise.allSettled` moved to stage 3, [#515](https://github.com/zloirock/core-js/issues/515)
- `String#replaceAll` moved to stage 2, behavior updated by the spec draft, [#524](https://github.com/zloirock/core-js/issues/524)
- `Promise.any` moved to stage 1, [#517](https://github.com/zloirock/core-js/issues/517)
- Removed `es.regexp.flags` dependency from `es.regexp.to-string`, [#536](https://github.com/zloirock/core-js/issues/536), [#537](https://github.com/zloirock/core-js/issues/537)
- Fixed IE8- non-enumerable properties support in `Object.{ assign, entries, values }`, [#541](https://github.com/zloirock/core-js/issues/541)
- Fixed support of primitives in `Object.getOwnPropertySymbols` in Chrome 38 / 39, [#539](https://github.com/zloirock/core-js/issues/539)
- `window.postMessage`-based task implementation uses location origin over `'*'`, [#542](https://github.com/zloirock/core-js/issues/542)
- Lookup `PromiseConstructor.resolve` only once in `Promise` combinators, [tc39/ecma262#1506](https://github.com/tc39/ecma262/pull/1506)
- Temporarily removed `core-js` dependency from `core-js-compat` since it's required for missed at this moment feature
- Show a message on `postinstall`
- Added compat data for Chrome 76, FF 67, Node 12

##### 2.6.6 [LEGACY] - 2019.05.20
- Fixed IE8- non-enumerable properties support in `Object.{ assign, entries, values }`, [#541](https://github.com/zloirock/core-js/issues/541)
- Fixed support of primitives in `Object.getOwnPropertySymbols` in Chrome 38 / 39, [#539](https://github.com/zloirock/core-js/issues/539)
- Show a message on `postinstall`

##### 3.0.1 - 2019.04.06
- Fixed some cases of work with malformed URI sequences in `URLSearchParams`, [#525](https://github.com/zloirock/core-js/issues/525)
- Added a workaround for a rollup issue, [#513](https://github.com/zloirock/core-js/issues/513)

##### 3.0.0 - 2019.03.19
- Features
  - Add new features:
    - `Object.fromEntries` ([ECMAScript 2019](https://github.com/tc39/proposal-object-from-entries))
    - `Symbol#description` ([ECMAScript 2019](https://tc39.es/ecma262/#sec-symbol.prototype.description))
    - New `Set` methods ([stage 2 proposal](https://github.com/tc39/proposal-set-methods))
      - `Set#difference`
      - `Set#intersection`
      - `Set#isDisjointFrom`
      - `Set#isSubsetOf`
      - `Set#isSupersetOf`
      - `Set#symmetricDifference`
      - `Set#union`
    - `Promise.allSettled` ([stage 2 proposal](https://github.com/tc39/proposal-promise-allSettled))
    - Getting last item from `Array` ([stage 1 proposal](https://github.com/keithamus/proposal-array-last))
      - `Array#lastItem`
      - `Array#lastIndex`
    - `String#replaceAll` ([stage 1 proposal](https://github.com/tc39/proposal-string-replace-all))
    - `String#codePoints` ([stage 1 proposal](https://github.com/tc39/proposal-string-prototype-codepoints))
    - New collections methods ([stage 1 proposal](https://github.com/tc39/collection-methods))
      - `Map.groupBy`
      - `Map.keyBy`
      - `Map#deleteAll`
      - `Map#every`
      - `Map#filter`
      - `Map#find`
      - `Map#findKey`
      - `Map#includes`
      - `Map#keyOf`
      - `Map#mapKeys`
      - `Map#mapValues`
      - `Map#merge`
      - `Map#reduce`
      - `Map#some`
      - `Map#update`
      - `Set#addAll`
      - `Set#deleteAll`
      - `Set#every`
      - `Set#filter`
      - `Set#find`
      - `Set#join`
      - `Set#map`
      - `Set#reduce`
      - `Set#some`
      - `WeakMap#deleteAll`
      - `WeakSet#addAll`
      - `WeakSet#deleteAll`
    - `compositeKey` and `compositeSymbol` methods ([stage 1 proposal](https://github.com/tc39/proposal-richer-keys/tree/master/compositeKey))
    - `Number.fromString` ([stage 1 proposal](https://github.com/tc39/proposal-number-fromstring))
    - `Math.seededPRNG` ([stage 1 proposal](https://github.com/tc39/proposal-seeded-random))
    - `Symbol.patternMatch` ([for stage 1 pattern matching proposal](https://github.com/tc39/proposal-pattern-matching))
    - `Symbol.dispose` ([for stage 1 `using` statement proposal](https://github.com/tc39/proposal-using-statement))
    - `Promise.any` (with `AggregateError`) ([stage 0 proposal](https://github.com/tc39/proposal-promise-any))
    - `URL` and `URLSearchParam` [from `URL` standard](https://url.spec.whatwg.org/), also [stage 0 proposal to ECMAScript](https://github.com/jasnell/proposal-url)
      - `URL`
        - `URL#href`
        - `URL#origin`
        - `URL#protocol`
        - `URL#username`
        - `URL#password`
        - `URL#host`
        - `URL#hostname`
        - `URL#port`
        - `URL#pathname`
        - `URL#search`
        - `URL#searchParams`
        - `URL#hash`
        - `URL#toString`
        - `URL#toJSON`
      - `URLSearchParams`
        - `URLSearchParams#append`
        - `URLSearchParams#delete`
        - `URLSearchParams#get`
        - `URLSearchParams#getAll`
        - `URLSearchParams#has`
        - `URLSearchParams#set`
        - `URLSearchParams#sort`
        - `URLSearchParams#toString`
        - `URLSearchParams#keys`
        - `URLSearchParams#values`
        - `URLSearchParams#entries`
        - `URLSearchParams#@@iterator`
    - `.forEach` method on iterable DOM collections ([#329](https://github.com/zloirock/core-js/issues/329))
  - Improve existing features:
    - Add triggering unhandled `Promise` rejection events (instead of only global handlers), [#205](https://github.com/zloirock/core-js/issues/205).
    - Wrap `fetch` for correct with polyfilled `Promise` and preventing problems like [#178](https://github.com/zloirock/core-js/issues/178), [#332](https://github.com/zloirock/core-js/issues/332), [#371](https://github.com/zloirock/core-js/issues/371).
    - Add support of `@@isConcatSpreadable` to `Array#concat`.
    - Add support of `@@species` to `Array#{concat, filter, map, slice, splice}`.
    - Add direct `.exec` calling to `RegExp#{@@replace, @@split, @@match, @@search}`. Also, added fixes for `RegExp#exec` method. [#411](https://github.com/zloirock/core-js/issues/411), [#434](https://github.com/zloirock/core-js/issues/434), [#453](https://github.com/zloirock/core-js/issues/453), thanks [**@nicolo-ribaudo**](https://github.com/nicolo-ribaudo).
    - Correct iterators prototypes chain, related [#261](https://github.com/zloirock/core-js/issues/261).
    - Correct Typed Arrays prototypes chain, related [#378](https://github.com/zloirock/core-js/issues/378).
    - Make the internal state of polyfilled features completely unobservable, [#146](https://github.com/zloirock/core-js/issues/146).
    - Add validation of receiver's internal class to missed non-generic methods.
    - Fix descriptors of global properties.
    - In the version without global pollution, if `Object#toString` does not support `@@toStringTag`, add to wrapped prototypes own `toString` method with `@@toStringTag` logic, see [#199](https://github.com/zloirock/core-js/issues/199).
  - Update standard features and proposals:
    - `asap` (old stage 0 proposal) replaced by `queueMicrotask` ([a part of HTML spec](https://html.spec.whatwg.org/multipage/timers-and-user-prompts.html#dom-queuemicrotask))
    - Update [`Observable`](https://github.com/tc39/proposal-observable) (#257, #276, etc.)
    - Update `Array#flatten` -> `Array#flat` and `Array#flatMap`
    - Update `global` [stage 3 proposal](https://github.com/tc39/proposal-global) - rename `global` to `globalThis`
    - Update `String#matchAll` ([proposal-string-matchall#17](https://github.com/tc39/proposal-string-matchall/pull/17), [proposal-string-matchall#38](https://github.com/tc39/proposal-string-matchall/pull/38), [proposal-string-matchall#41](https://github.com/tc39/proposal-string-matchall/pull/41), etc.) and move to the stage 3
    - Update `.name` properties of `String#{trimStart, trimEnd , trimLeft, trimRight}`, move to the stage 3
    - Remove mongolian vowel separator (U+180E) from the list of whitespaces for methods like `String#trim` (ES6 -> ES7)
  - Mark ES2016, ES2017, ES2018, ES2019 features as stable:
    - `Array#{ flat, flatMap }`
    - `{ Array, %TypedArray% }#includes`
    - `Object.{ values, entries}`
    - `Object.getOwnPropertyDescriptors`
    - `String#{ padStart, padEnd }`
    - `String#{ trimStart, trimEnd, trimLeft, trimRight }`
    - `Promise#finally`
    - `Symbol.asyncIterator`
    - `Object#__(define|lookup)[GS]etter__`
  - Remove obsolete features:
    - `Error.isError` (withdrawn)
    - `System.global` and `global` (replaced by `globalThis`)
    - `Map#toJSON` and `Set#toJSON` (rejected)
    - `RegExp.escape` (rejected)
    - `Reflect.enumerate` (removed from the spec)
    - Unnecessary iteration methods from `CSSRuleList`, `MediaList`, `StyleSheetList`
  - **No more non-standard features**, finally removed:
    - `Dict`
    - `Object.{classof, isObject, define, make}`
    - `Function#part`
    - `Number#@@iterator`
    - `String#{escapeHTML, unescapeHTML}`
    - `delay`
  - Add `.sham` flag to features which can't be properly polyfilled and / or not recommended for usage:
    - `Symbol` constructor - we can't add new primitives. `Object.prototype` accessors too expensive.
    - `Object.{create, defineProperty, defineProperties, getOwnPropertyDescriptor, getOwnPropertyDescriptos}`, `Reflect.{defineProperty, getOwnPropertyDescriptor}` can't be properly polyfilled without descriptors support.
    - `Object.{freeze, seal, preventExtensions}`, `Reflect.preventExtensions` can't be properly polyfilled in ES3 environment.
    - `Object.getPrototypeOf` can be deceived in ES3 environment.
    - `Reflect.construct` can't be polyfilled for a correct work with `newTarget` argument on built-ins.
    - Typed Array constructors polyfill is quite correct but too expensive.
    - `URL` constructor in engines without descriptors support.
- Bug and compatibility fixes:
  - Fix deoptimisation of iterators in V8, [#377](https://github.com/zloirock/core-js/issues/377).
  - Fix import of property before constructor which should contain this property, [#262](https://github.com/zloirock/core-js/issues/262).
  - Fix some cases of IE11 `WeakMap` frozen keys fallback, [#384](https://github.com/zloirock/core-js/issues/384).
  - Fix non-enumerable integer keys issue because of Nashorn ~ JDK8 bug, [#389](https://github.com/zloirock/core-js/issues/389).
  - Fix [Safari 12.0 `Array#reverse` bug](https://bugs.webkit.org/show_bug.cgi?id=188794).
  - One more fix for microtasks in iOS related [#339](https://github.com/zloirock/core-js/issues/339).
  - Added a fallback for [Rhino bug](https://github.com/mozilla/rhino/issues/346), [#440](https://github.com/zloirock/core-js/issues/440).
  - Many other internal fixes and improvements.
- Repository:
  - Change `core-js` repository structure to monorepo with packages in `/packages/` directory.
  - Clean-up it, remove all possible duplicates, generated files, etc.
- Packages:
  - **Extract a version without global namespace pollution to a separate `core-js-pure` package (replacement for `core-js/library`).**
  - **Leave only one pair of bundles (global, with all polyfills) and move it to `core-js-bundle` package.**
  - Remove bundling logic from `core-js` package, leave it only in `core-js-builder` package.
  - Clean-up packages.
  - Because of all approaches, **reduce size of packages from ~2mb for `core-js@2` to**:
    - **~500kb for `core-js` package**
    - **~440kb for `core-js-pure` package**
  - Finally remove `bower.json`
- CommonJS API, namespaces:
  - Add availability [configuration of aggressiveness](https://github.com/zloirock/core-js/blob/master/README.md#configurable-level-of-aggressiveness).
  - Move `core-js/library` to separate `core-js-pure` package.
  - Because of removing all non-standard features, we no longer need `core-js/shim` entry point, replace it just with `core-js`.
  - Move all features from ES5, ES2015, ES2016, ES2017, ES2018 and ES2019 to one namespace for stable ES - it's available as `core-js/es`, all those features in `modules` folder has `es.` prefix.
  - Change prefix for ES proposals from `es7.` to `esnext.`, they no longer available in `core-js/es7`, use `core-js/stage/*` instead of that.
  - Rename `core-js(/library)/fn` to `core-js(-pure)/features` for improve readability.
  - Allow more granular inclusion of features from `/es/` path (for example, `core-js/es/array/from`).
  - Add `/stable/` entry points as an equal of `/features/` for stable features, without proposals.
  - Add `/proposals/` entry points for allow include all features from one proposal (for example, `core-js/proposals/reflect-metadata`).
  - Add `/es|stable|features/instance/` entry points for getting polyfill of the related method for passed instance (could be used in cases like `babel-runtime`).
  - Split typed arrays polyfills. Now you can, for example, load only required method (for example, `core-js/es/typed-array/from`).
  - Extract well-known symbols definition from `es.symbol` module for loading only required features, for example, in MS Edge.
  - Rename `web.dom` namespace to `web.dom-collections`.
  - Rename `es6.regexp.{match, replace, search, split}` -> `es.string.{match, replace, search, split}` - mainly it's fixes / adding support of well-known symbols to string methods, only in second place adding related methods to regexp prototype.
  - Relax `/modules/` directory by moving internal modules to `/internals/` directory.
  - Remove deprecated array entry points: `core-js(/library)/fn/array/{pop, push, reverse, shift, unshift}`.
  - `core` object no longer available in the global version, entry points which previously returned it now returns `globalThis` object. Also, don't set global `core` property.
  - Add some missing entry points.
- Tools, tests, code quality:
  - Added `core-js-compat` package with:
    - Data about the necessity of `core-js` modules and API for getting a list of required `core-js` modules by `browserslist` query, [#466](https://github.com/zloirock/core-js/issues/466).
    - Data which modules load by each entry point (mainly useful for tools like `@babel/preset-env`).
    - Data which modules added in minor versions (mainly useful for tools like `@babel/preset-env`).
  - `core-js-builder` package:
    - Added `targets` option with `browserslist` query.
    - Removed an option for generation bundle of a version without global namespace pollution - now it's an odd use case.
    - Removed UMD wrapper from a generated code of bundles - we don't need it for a global polyfill.
  - **Getting rid of LiveScript**, usage another language in JS standard library looks strange and impedes usage of tools like ESLint:
    - Tests are rewritten to JS.
    - Scripts are rewritten to JS.
  - Babel with minimalistic config (which should work anywhere) used on tests.
  - ESLint used on tests and tools.
  - Source code refactored for improving readability.

##### 2.6.5 - 2019.02.15
- Fixed buggy `String#padStart` and `String#padEnd` mobile Safari implementations, [#414](https://github.com/zloirock/core-js/issues/414).

##### 2.6.4 - 2019.02.07
- Added a workaround against crushing an old IE11.0.9600.16384 build, [#485](https://github.com/zloirock/core-js/issues/485).

##### 2.6.3 - 2019.01.22
- Added a workaround for `babel-minify` bug, [#479](https://github.com/zloirock/core-js/issues/479)

##### 2.6.2 - 2019.01.10
- Fixed handling of `$` in `String#replace`, [#471](https://github.com/zloirock/core-js/issues/471)

##### 2.6.1 - 2018.12.18
- Fixed an issue with minified version, [#463](https://github.com/zloirock/core-js/issues/463), [#465](https://github.com/zloirock/core-js/issues/465)

##### 2.6.0 - 2018.12.05
- Add direct `.exec` calling to `RegExp#{@@replace, @@split, @@match, @@search}`. Also, added fixes for `RegExp#exec` method. [#428](https://github.com/zloirock/core-js/issues/428), [#435](https://github.com/zloirock/core-js/issues/435), [#458](https://github.com/zloirock/core-js/issues/458), thanks [**@nicolo-ribaudo**](https://github.com/nicolo-ribaudo).

##### 2.5.7 - 2018.05.26
- Get rid of reserved variable name `final`, related [#400](https://github.com/zloirock/core-js/issues/400)

##### 2.5.6 - 2018.05.07
- Forced replace native `Promise` in V8 6.6 (Node 10 and Chrome 66) because of [a bug with resolving custom thenables](https://bugs.chromium.org/p/chromium/issues/detail?id=830565)
- Added a workaround for usage buggy native LG WebOS 2 `Promise` in microtask implementation, [#396](https://github.com/zloirock/core-js/issues/396)
- Added modern version internal debugging information about used versions

##### 2.5.5 - 2018.04.08
- Fix some edge cases of `Reflect.set`, [#392](https://github.com/zloirock/core-js/issues/392) and [#393](https://github.com/zloirock/core-js/issues/393)

##### 2.5.4 - 2018.03.27
- Fixed one case of deoptimization built-in iterators in V8, related [#377](https://github.com/zloirock/core-js/issues/377)
- Fixed some cases of iterators feature detection, [#368](https://github.com/zloirock/core-js/issues/368)
- Fixed manually entered NodeJS domains issue in `Promise`, [#367](https://github.com/zloirock/core-js/issues/367)
- Fixed `Number.{parseInt, parseFloat}` entry points
- Fixed `__(define|lookup)[GS]etter__` export in the `library` version

##### 2.5.3 - 2017.12.12
- Fixed calling `onunhandledrejectionhandler` multiple times for one `Promise` chain, [#318](https://github.com/zloirock/core-js/issues/318)
- Forced replacement of `String#{padStart, padEnd}` in Safari 10 because of [a bug](https://bugs.webkit.org/show_bug.cgi?id=161944), [#280](https://github.com/zloirock/core-js/issues/280)
- Fixed `Array#@@iterator` in a very rare version of `WebKit`, [#236](https://github.com/zloirock/core-js/issues/236) and [#237](https://github.com/zloirock/core-js/issues/237)
- One more [#345](https://github.com/zloirock/core-js/issues/345)-related fix

##### 2.5.2 - 2017.12.09
- `MutationObserver` no longer used for microtask implementation in iOS Safari because of bug with scrolling, [#339](https://github.com/zloirock/core-js/issues/339)
- Fixed `JSON.stringify(undefined, replacer)` case in the wrapper from the `Symbol` polyfill, [#345](https://github.com/zloirock/core-js/issues/345)
- `Array()` calls changed to `new Array()` for V8 optimisation

##### 2.5.1 - 2017.09.01
- Updated `Promise#finally` per [tc39/proposal-promise-finally#37](https://github.com/tc39/proposal-promise-finally/issues/37)
- Optimized usage of some internal helpers for reducing size of `shim` version
- Fixed some entry points for virtual methods

##### 2.5.0 - 2017.08.05
- Added `Promise#finally` [stage 3 proposal](https://github.com/tc39/proposal-promise-finally), [#225](https://github.com/zloirock/core-js/issues/225)
- Added `Promise.try` [stage 1 proposal](https://github.com/tc39/proposal-promise-try)
- Added `Array#flatten` and `Array#flatMap` [stage 1 proposal](https://tc39.github.io/proposal-flatMap)
- Added `.of` and `.from` methods on collection constructors [stage 1 proposal](https://github.com/tc39/proposal-setmap-offrom):
  - `Map.of`
  - `Set.of`
  - `WeakSet.of`
  - `WeakMap.of`
  - `Map.from`
  - `Set.from`
  - `WeakSet.from`
  - `WeakMap.from`
- Added `Math` extensions [stage 1 proposal](https://github.com/rwaldron/proposal-math-extensions), [#226](https://github.com/zloirock/core-js/issues/226):
  - `Math.clamp`
  - `Math.DEG_PER_RAD`
  - `Math.degrees`
  - `Math.fscale`
  - `Math.RAD_PER_DEG`
  - `Math.radians`
  - `Math.scale`
- Added `Math.signbit` [stage 1 proposal](http://jfbastien.github.io/papers/Math.signbit.html)
- Updated `global` [stage 3 proposal](https://github.com/tc39/proposal-global) - added `global` global object, `System.global` deprecated
- Updated `Object.getOwnPropertyDescriptors` to the [final version](https://tc39.es/ecma262/2017/#sec-object.getownpropertydescriptors) - it should not create properties if descriptors are `undefined`
- Updated the list of iterable DOM collections, [#249](https://github.com/zloirock/core-js/issues/249), added:
  - `CSSStyleDeclaration#@@iterator`
  - `CSSValueList#@@iterator`
  - `ClientRectList#@@iterator`
  - `DOMRectList#@@iterator`
  - `DOMStringList#@@iterator`
  - `DataTransferItemList#@@iterator`
  - `FileList#@@iterator`
  - `HTMLAllCollection#@@iterator`
  - `HTMLCollection#@@iterator`
  - `HTMLFormElement#@@iterator`
  - `HTMLSelectElement#@@iterator`
  - `MimeTypeArray#@@iterator`
  - `NamedNodeMap#@@iterator`
  - `PaintRequestList#@@iterator`
  - `Plugin#@@iterator`
  - `PluginArray#@@iterator`
  - `SVGLengthList#@@iterator`
  - `SVGNumberList#@@iterator`
  - `SVGPathSegList#@@iterator`
  - `SVGPointList#@@iterator`
  - `SVGStringList#@@iterator`
  - `SVGTransformList#@@iterator`
  - `SourceBufferList#@@iterator`
  - `TextTrackCueList#@@iterator`
  - `TextTrackList#@@iterator`
  - `TouchList#@@iterator`
- Updated stages of proposals:
  - [`Object.getOwnPropertyDescriptors`](https://github.com/tc39/proposal-object-getownpropertydescriptors) to [stage 4 (ES2017)](https://tc39.es/ecma262/2017/#sec-object.getownpropertydescriptors)
  - [String padding](https://github.com/tc39/proposal-string-pad-start-end) to [stage 4 (ES2017)](https://tc39.es/ecma262/2017/#sec-string.prototype.padend)
  - [`global`](https://github.com/tc39/proposal-global) to [stage 3](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-09/sept-28.md#revisit-systemglobal--global)
  - [String trimming](https://github.com/tc39/proposal-string-left-right-trim) to [stage 2](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-07/jul-27.md#10iic-trimstarttrimend)
- Updated typed arrays to the modern (ES2016+) arguments validation, 
[#293](https://github.com/zloirock/core-js/pull/293)
- Fixed `%TypedArray%.from` Safari bug, [#285](https://github.com/zloirock/core-js/issues/285)
- Fixed compatibility with old version of Prototype.js, [#278](https://github.com/zloirock/core-js/issues/278), [#289](https://github.com/zloirock/core-js/issues/289)
- `Function#name` no longer cache the result for correct behaviour with inherited constructors, [#296](https://github.com/zloirock/core-js/issues/296)
- Added errors on incorrect context of collection methods, [#272](https://github.com/zloirock/core-js/issues/272)
- Fixed conversion typed array constructors to string, fix [#300](https://github.com/zloirock/core-js/issues/300)
- Fixed `Set#size` with debugger ReactNative for Android, [#297](https://github.com/zloirock/core-js/issues/297)
- Fixed an issue with Electron-based debugger, [#230](https://github.com/zloirock/core-js/issues/230)
- Fixed compatibility with incomplete third-party `WeakMap` polyfills, [#252](https://github.com/zloirock/core-js/pull/252)
- Added a fallback for `Date#toJSON` in engines without native `Date#toISOString`, [#220](https://github.com/zloirock/core-js/issues/220)
- Added support for Sphere Dispatch API, [#286](https://github.com/zloirock/core-js/pull/286)
- Seriously changed the coding style and the [ESLint config](https://github.com/zloirock/core-js/blob/master/.eslintrc.js)
- Updated many dev dependencies (`webpack`, `uglify`, etc)
- Some other minor fixes and optimizations

##### 2.4.1 - 2016.07.18
- Fixed `script` tag for some parsers, [#204](https://github.com/zloirock/core-js/issues/204), [#216](https://github.com/zloirock/core-js/issues/216)
- Removed some unused variables, [#217](https://github.com/zloirock/core-js/issues/217), [#218](https://github.com/zloirock/core-js/issues/218)
- Fixed MS Edge `Reflect.construct` and `Reflect.apply` - they should not allow primitive as `argumentsList` argument

##### 1.2.7 [LEGACY] - 2016.07.18
- Some fixes for issues like [#159](https://github.com/zloirock/core-js/issues/159), [#186](https://github.com/zloirock/core-js/issues/186), [#194](https://github.com/zloirock/core-js/issues/194), [#207](https://github.com/zloirock/core-js/issues/207)

##### 2.4.0 - 2016.05.08
- Added `Observable`, [stage 1 proposal](https://github.com/zenparsing/es-observable)
- Fixed behavior `Object.{getOwnPropertySymbols, getOwnPropertyDescriptor}` and `Object#propertyIsEnumerable` on `Object.prototype`
- `Reflect.construct` and `Reflect.apply` should throw an error if `argumentsList` argument is not an object, [#194](https://github.com/zloirock/core-js/issues/194)

##### 2.3.0 - 2016.04.24
- Added `asap` for enqueuing microtasks, [stage 0 proposal](https://github.com/rwaldron/tc39-notes/blob/master/es6/2014-09/sept-25.md#510-globalasap-for-enqueuing-a-microtask)
- Added well-known symbol `Symbol.asyncIterator` for [stage 2 async iteration proposal](https://github.com/tc39/proposal-async-iteration)
- Added well-known symbol `Symbol.observable` for [stage 1 observables proposal](https://github.com/zenparsing/es-observable)
- `String#{padStart, padEnd}` returns original string if filler is empty string, [TC39 meeting notes](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-03/march-29.md#stringprototypepadstartpadend)
- `Object.values` and `Object.entries` moved to stage 4 from 3, [TC39 meeting notes](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-03/march-29.md#objectvalues--objectentries)
- `System.global` moved to stage 2 from 1, [TC39 meeting notes](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-03/march-29.md#systemglobal)
- `Map#toJSON` and `Set#toJSON` rejected and will be removed from the next major release, [TC39 meeting notes](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-03/march-31.md#mapprototypetojsonsetprototypetojson)
- `Error.isError` withdrawn and will be removed from the next major release, [TC39 meeting notes](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-03/march-29.md#erroriserror)
- Added fallback for `Function#name` on non-extensible functions and functions with broken `toString` conversion, [#193](https://github.com/zloirock/core-js/issues/193)

##### 2.2.2 - 2016.04.06
- Added conversion `-0` to `+0` to `Array#{indexOf, lastIndexOf}`, [ES2016 fix](https://github.com/tc39/ecma262/pull/316)
- Added fixes for some `Math` methods in Tor Browser
- `Array.{from, of}` no longer calls prototype setters
- Added workaround over Chrome DevTools strange behavior, [#186](https://github.com/zloirock/core-js/issues/186)

##### 2.2.1 - 2016.03.19
- Fixed `Object.getOwnPropertyNames(window)` `2.1+` versions bug, [#181](https://github.com/zloirock/core-js/issues/181)

##### 2.2.0 - 2016.03.15
- Added `String#matchAll`, [proposal](https://github.com/tc39/String.prototype.matchAll)
- Added `Object#__(define|lookup)[GS]etter__`, [annex B ES2017](https://github.com/tc39/ecma262/pull/381)
- Added `@@toPrimitive` methods to `Date` and `Symbol`
- Fixed `%TypedArray%#slice` in Edge ~ 13 (throws with `@@species` and wrapped / inherited constructor)
- Some other minor fixes

##### 2.1.5 - 2016.03.12
- Improved support NodeJS domains in `Promise#then`, [#180](https://github.com/zloirock/core-js/issues/180)
- Added fallback for `Date#toJSON` bug in Qt Script, [#173](https://github.com/zloirock/core-js/issues/173#issuecomment-193972502)

##### 2.1.4 - 2016.03.08
- Added fallback for `Symbol` polyfill in Qt Script, [#173](https://github.com/zloirock/core-js/issues/173)
- Added one more fallback for IE11 `Script Access Denied` error with iframes, [#165](https://github.com/zloirock/core-js/issues/165)

##### 2.1.3 - 2016.02.29
- Added fallback for [`es6-promise` package bug](https://github.com/stefanpenner/es6-promise/issues/169), [#176](https://github.com/zloirock/core-js/issues/176)

##### 2.1.2 - 2016.02.29
- Some minor `Promise` fixes:
  - Browsers `rejectionhandled` event better HTML spec complaint
  - Errors in unhandled rejection handlers should not cause any problems
  - Fixed typo in feature detection

##### 2.1.1 - 2016.02.22
- Some `Promise` improvements:
  - Feature detection:
    - **Added detection unhandled rejection tracking support - now it's available everywhere**, [#140](https://github.com/zloirock/core-js/issues/140)
    - Added detection `@@species` pattern support for completely correct subclassing
    - Removed usage `Object.setPrototypeOf` from feature detection and noisy console message about it in FF
  - `Promise.all` fixed for some very specific cases

##### 2.1.0 - 2016.02.09
- **API**:
  - ES5 polyfills are split and logic, used in other polyfills, moved to internal modules
    - **All entry point works in ES3 environment like IE8- without `core-js/(library/)es5`**
    - **Added all missed single entry points for ES5 polyfills**
    - Separated ES5 polyfills moved to the ES6 namespace. Why?
      - Mainly, for prevent duplication features in different namespaces - logic of most required ES5 polyfills changed in ES6+:
        - Already added changes for: `Object` statics - should accept primitives, new whitespaces lists in `String#trim`, `parse(Int|float)`, `RegExp#toString` logic, `String#split`, etc
        - Should be changed in the future: `@@species` and `ToLength` logic in `Array` methods, `Date` parsing, `Function#bind`, etc
        - Should not be changed only several features like `Array.isArray` and `Date.now`
      - Some ES5 polyfills required for modern engines
    - All old entry points should work fine, but in the next major release API can be changed
  - `Object.getOwnPropertyDescriptors` moved to the stage 3, [January TC39 meeting](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-01/2016-01-28.md#objectgetownpropertydescriptors-to-stage-3-jordan-harband-low-priority-but-super-quick)
  - Added `umd` option for [custom build process](https://github.com/zloirock/core-js#custom-build-from-external-scripts), [#169](https://github.com/zloirock/core-js/issues/169)
  - Returned entry points for `Array` statics, removed in `2.0`, for compatibility with `babel` `6` and for future fixes
- **Deprecated**:
  - `Reflect.enumerate` deprecated and will be removed from the next major release, [January TC39 meeting](https://github.com/rwaldron/tc39-notes/blob/master/es7/2016-01/2016-01-28.md#5xix-revisit-proxy-enumerate---revisit-decision-to-exhaust-iterator)
- **New Features**:
  - Added [`Reflect` metadata API](https://github.com/jonathandturner/decorators/blob/master/specs/metadata.md) as a pre-strawman feature, [#152](https://github.com/zloirock/core-js/issues/152):
    - `Reflect.defineMetadata`
    - `Reflect.deleteMetadata`
    - `Reflect.getMetadata`
    - `Reflect.getMetadataKeys`
    - `Reflect.getOwnMetadata`
    - `Reflect.getOwnMetadataKeys`
    - `Reflect.hasMetadata`
    - `Reflect.hasOwnMetadata`
    - `Reflect.metadata`
  - Implementation / fixes `Date#toJSON`
  - Fixes for `parseInt` and `Number.parseInt`
  - Fixes for `parseFloat` and `Number.parseFloat`
  - Fixes for `RegExp#toString`
  - Fixes for `Array#sort`
  - Fixes for `Number#toFixed`
  - Fixes for `Number#toPrecision`
  - Additional fixes for `String#split` (`RegExp#@@split`)
- **Improvements**:
  - Correct subclassing wrapped collections, `Number` and `RegExp` constructors with native class syntax
  - Correct support `SharedArrayBuffer` and buffers from other realms in typed arrays wrappers 
  - Additional validations for `Object.{defineProperty, getOwnPropertyDescriptor}` and `Reflect.defineProperty`
- **Bug Fixes**:
  - Fixed some cases `Array#lastIndexOf` with negative second argument

##### 2.0.3 - 2016.01.11
- Added fallback for V8 ~ Chrome 49 `Promise` subclassing bug causes unhandled rejection on feature detection, [#159](https://github.com/zloirock/core-js/issues/159)
- Added fix for very specific environments with global `window === null`

##### 2.0.2 - 2016.01.04
- Temporarily removed `length` validation from `Uint8Array` constructor wrapper. Reason - [bug in `ws` module](https://github.com/websockets/ws/pull/645) (-> `socket.io`) which passes to `Buffer` constructor -> `Uint8Array` float and uses [the `V8` bug](https://code.google.com/p/v8/issues/detail?id=4552) for conversion to int (by the spec should be thrown an error). [It creates problems for many people.](https://github.com/karma-runner/karma/issues/1768) I hope, it will be returned after fixing this bug in `V8`.

##### 2.0.1 - 2015.12.31
- Forced usage `Promise.resolve` polyfill in the `library` version for correct work with wrapper
- `Object.assign` should be defined in the strict mode -> throw an error on extension non-extensible objects, [#154](https://github.com/zloirock/core-js/issues/154)

##### 2.0.0 - 2015.12.24
- Added implementations and fixes [Typed Arrays](https://github.com/zloirock/core-js#ecmascript-6-typed-arrays)-related features
  - `ArrayBuffer`, `ArrayBuffer.isView`, `ArrayBuffer#slice`
  - `DataView` with all getter / setter methods
  - `Int8Array`, `Uint8Array`, `Uint8ClampedArray`, `Int16Array`, `Uint16Array`, `Int32Array`, `Uint32Array`, `Float32Array` and `Float64Array` constructors
  - `%TypedArray%.{for, of}`, `%TypedArray%#{copyWithin, every, fill, filter, find, findIndex, forEach, indexOf, includes, join, lastIndexOf, map, reduce, reduceRight, reverse, set, slice, some, sort, subarray, values, keys, entries, @@iterator, ...}`
- Added [`System.global`](https://github.com/zloirock/core-js#ecmascript-7-proposals), [proposal](https://github.com/tc39/proposal-global), [November TC39 meeting](https://github.com/rwaldron/tc39-notes/tree/master/es7/2015-11/nov-19.md#systemglobal-jhd)
- Added [`Error.isError`](https://github.com/zloirock/core-js#ecmascript-7-proposals), [proposal](https://github.com/ljharb/proposal-is-error), [November TC39 meeting](https://github.com/rwaldron/tc39-notes/tree/master/es7/2015-11/nov-19.md#jhd-erroriserror)
- Added [`Math.{iaddh, isubh, imulh, umulh}`](https://github.com/zloirock/core-js#ecmascript-7-proposals), [proposal](https://gist.github.com/BrendanEich/4294d5c212a6d2254703)
- `RegExp.escape` moved from the `es7` to the non-standard `core` namespace, [July TC39 meeting](https://github.com/rwaldron/tc39-notes/blob/master/es7/2015-07/july-28.md#62-regexpescape) - too slow, but it's condition of stability, [#116](https://github.com/zloirock/core-js/issues/116)
- [`Promise`](https://github.com/zloirock/core-js#ecmascript-6-promise)
  - Some performance optimisations
  - Added basic support [`rejectionHandled` event / `onrejectionhandled` handler](https://github.com/zloirock/core-js#unhandled-rejection-tracking) to the polyfill
  - Removed usage `@@species` from `Promise.{all, race}`, [November TC39 meeting](https://github.com/rwaldron/tc39-notes/tree/master/es7/2015-11/nov-18.md#conclusionresolution-2)
- Some improvements [collections polyfills](https://github.com/zloirock/core-js#ecmascript-6-collections)
  - `O(1)` and preventing possible leaks with frozen keys, [#134](https://github.com/zloirock/core-js/issues/134)
  - Correct observable state object keys
- Renamed `String#{padLeft, padRight}` -> [`String#{padStart, padEnd}`](https://github.com/zloirock/core-js#ecmascript-7-proposals), [proposal](https://github.com/tc39/proposal-string-pad-start-end), [November TC39 meeting](https://github.com/rwaldron/tc39-notes/tree/master/es7/2015-11/nov-17.md#conclusionresolution-2) (they want to rename it on each meeting?O_o), [#132](https://github.com/zloirock/core-js/issues/132)
- Added [`String#{trimStart, trimEnd}` as aliases for `String#{trimLeft, trimRight}`](https://github.com/zloirock/core-js#ecmascript-7-proposals), [proposal](https://github.com/sebmarkbage/ecmascript-string-left-right-trim), [November TC39 meeting](https://github.com/rwaldron/tc39-notes/tree/master/es7/2015-11/nov-17.md#conclusionresolution-2)
- Added [annex B HTML methods](https://github.com/zloirock/core-js#ecmascript-6-string) - ugly, but also [the part of the spec](http://www.ecma-international.org/ecma-262/6.0/#sec-string.prototype.anchor)
- Added little fix for [`Date#toString`](https://github.com/zloirock/core-js#ecmascript-6-date) - `new Date(NaN).toString()` [should be `'Invalid Date'`](http://www.ecma-international.org/ecma-262/6.0/#sec-todatestring)
- Added [`{keys, values, entries, @@iterator}` methods to DOM collections](https://github.com/zloirock/core-js#iterable-dom-collections) which should have [iterable interface](https://heycam.github.io/webidl/#idl-iterable) or should be [inherited from `Array`](https://heycam.github.io/webidl/#LegacyArrayClass) - `NodeList`, `DOMTokenList`, `MediaList`, `StyleSheetList`, `CSSRuleList`.
- Removed Mozilla `Array` generics - [deprecated and will be removed from FF](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Array_generic_methods), [looks like strawman is dead](http://wiki.ecmascript.org/doku.php?id=strawman:array_statics), available [alternative shim](https://github.com/plusdude/array-generics)
- Removed `core.log` module
- CommonJS API
  - Added entry points for [virtual methods](https://github.com/zloirock/core-js#commonjs-and-prototype-methods-without-global-namespace-pollution)
  - Added entry points for [stages proposals](https://github.com/zloirock/core-js#ecmascript-7-proposals)
  - Some other minor changes
- [Custom build from external scripts](https://github.com/zloirock/core-js#custom-build-from-external-scripts) moved to the separate package for preventing problems with dependencies
- Changed `$` prefix for internal modules file names because Team Foundation Server does not support it, [#129](https://github.com/zloirock/core-js/issues/129)
- Additional fix for `SameValueZero` in V8 ~ Chromium 39-42 collections
- Additional fix for FF27 `Array` iterator
- Removed usage shortcuts for `arguments` object - old WebKit bug, [#150](https://github.com/zloirock/core-js/issues/150)
- `{Map, Set}#forEach` non-generic, [#144](https://github.com/zloirock/core-js/issues/144)
- Many other improvements

##### 1.2.6 - 2015.11.09
- Reject with `TypeError` on attempt resolve promise itself
- Correct behavior with broken `Promise` subclass constructors / methods
- Added `Promise`-based fallback for microtask
- Fixed V8 and FF `Array#{values, @@iterator}.name`
- Fixed IE7- `[1, 2].join(undefined) -> '1,2'`
- Some other fixes / improvements / optimizations

##### 1.2.5 - 2015.11.02
- Some more `Number` constructor fixes:
  - Fixed V8 ~ Node 0.8 bug: `Number('+0x1')` should be `NaN`
  - Fixed `Number(' 0b1\n')` case, should be `1`
  - Fixed `Number()` case, should be `0`

##### 1.2.4 - 2015.11.01
- Fixed `Number('0b12') -> NaN` case in the shim
- Fixed V8 ~ Chromium 40- bug - `Weak(Map|Set)#{delete, get, has}` should not throw errors [#124](https://github.com/zloirock/core-js/issues/124)
- Some other fixes and optimizations

##### 1.2.3 - 2015.10.23
- Fixed some problems related old V8 bug `Object('a').propertyIsEnumerable(0) // => false`, for example, `Object.assign({}, 'qwe')` from the last release
- Fixed `.name` property and `Function#toString` conversion some polyfilled methods
- Fixed `Math.imul` arity in Safari 8-

##### 1.2.2 - 2015.10.18
- Improved optimisations for V8
- Fixed build process from external packages, [#120](https://github.com/zloirock/core-js/pull/120)
- One more `Object.{assign, values, entries}` fix for [**very** specific case](https://github.com/ljharb/proposal-object-values-entries/issues/5)

##### 1.2.1 - 2015.10.02
- Replaced fix `JSON.stringify` + `Symbol` behavior from `.toJSON` method to wrapping `JSON.stringify` - little more correct, [compat-table/642](https://github.com/kangax/compat-table/pull/642)
- Fixed typo which broke tasks scheduler in WebWorkers in old FF, [#114](https://github.com/zloirock/core-js/pull/114)

##### 1.2.0 - 2015.09.27
- Added browser [`Promise` rejection hook](#unhandled-rejection-tracking), [#106](https://github.com/zloirock/core-js/issues/106)
- Added correct [`IsRegExp`](http://www.ecma-international.org/ecma-262/6.0/#sec-isregexp) logic to [`String#{includes, startsWith, endsWith}`](https://github.com/zloirock/core-js/#ecmascript-6-string) and [`RegExp` constructor](https://github.com/zloirock/core-js/#ecmascript-6-regexp), `@@match` case, [example](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/match#Disabling_the_isRegExp_check)
- Updated [`String#leftPad`](https://github.com/zloirock/core-js/#ecmascript-7-proposals) [with proposal](https://github.com/ljharb/proposal-string-pad-left-right/issues/6): string filler truncated from the right side
- Replaced V8 [`Object.assign`](https://github.com/zloirock/core-js/#ecmascript-6-object) - its properties order not only [incorrect](https://github.com/sindresorhus/object-assign/issues/22), it is non-deterministic and it causes some problems
- Fixed behavior with deleted in getters properties for `Object.{`[`assign`](https://github.com/zloirock/core-js/#ecmascript-6-object)`, `[`entries, values`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)`}`, [example](http://goo.gl/iQE01c)
- Fixed [`Math.sinh`](https://github.com/zloirock/core-js/#ecmascript-6-math) with very small numbers in V8 near Chromium 38
- Some other fixes and optimizations

##### 1.1.4 - 2015.09.05
- Fixed support symbols in FF34-35 [`Object.assign`](https://github.com/zloirock/core-js/#ecmascript-6-object)
- Fixed [collections iterators](https://github.com/zloirock/core-js/#ecmascript-6-iterators) in FF25-26
- Fixed non-generic WebKit [`Array.of`](https://github.com/zloirock/core-js/#ecmascript-6-array)
- Some other fixes and optimizations

##### 1.1.3 - 2015.08.29
- Fixed support Node.js domains in [`Promise`](https://github.com/zloirock/core-js/#ecmascript-6-promise), [#103](https://github.com/zloirock/core-js/issues/103)

##### 1.1.2 - 2015.08.28
- Added `toJSON` method to [`Symbol`](https://github.com/zloirock/core-js/#ecmascript-6-symbol) polyfill and to MS Edge implementation for expected `JSON.stringify` result w/o patching this method
- Replaced [`Reflect.construct`](https://github.com/zloirock/core-js/#ecmascript-6-reflect) implementations w/o correct support third argument
- Fixed `global` detection with changed `document.domain` in ~IE8, [#100](https://github.com/zloirock/core-js/issues/100)

##### 1.1.1 - 2015.08.20
- Added more correct microtask implementation for [`Promise`](#ecmascript-6-promise)

##### 1.1.0 - 2015.08.17
- Updated [string padding](https://github.com/zloirock/core-js/#ecmascript-7-proposals) to [actual proposal](https://github.com/ljharb/proposal-string-pad-left-right) - renamed, minor internal changes:
  - `String#lpad` -> `String#padLeft`
  - `String#rpad` -> `String#padRight`
- Added [string trim functions](#ecmascript-7-proposals) - [proposal](https://github.com/sebmarkbage/ecmascript-string-left-right-trim), defacto standard - required only for IE11- and fixed for some old engines:
  - `String#trimLeft`
  - `String#trimRight`
- [`String#trim`](https://github.com/zloirock/core-js/#ecmascript-6-string) fixed for some engines by es6 spec and moved from `es5` to single `es6` module
- Splitted [`es6.object.statics-accept-primitives`](https://github.com/zloirock/core-js/#ecmascript-6-object)
- Caps for `freeze`-family `Object` methods moved from `es5` to `es6` namespace and joined with [es6 wrappers](https://github.com/zloirock/core-js/#ecmascript-6-object)
- `es5` [namespace](https://github.com/zloirock/core-js/#commonjs) also includes modules, moved to `es6` namespace - you can use it as before
- Increased `MessageChannel` priority in `$.task`, [#95](https://github.com/zloirock/core-js/issues/95)
- Does not get `global.Symbol` on each getting iterator, if you wanna use alternative `Symbol` shim - add it before `core-js`
- [`Reflect.construct`](https://github.com/zloirock/core-js/#ecmascript-6-reflect) optimized and fixed for some cases
- Simplified [`Reflect.enumerate`](https://github.com/zloirock/core-js/#ecmascript-6-reflect), see [this question](https://esdiscuss.org/topic/question-about-enumerate-and-property-decision-timing)
- Some corrections in [`Math.acosh`](https://github.com/zloirock/core-js/#ecmascript-6-math)
- Fixed [`Math.imul`](https://github.com/zloirock/core-js/#ecmascript-6-math) for old WebKit
- Some fixes in string / RegExp [well-known symbols](https://github.com/zloirock/core-js/#ecmascript-6-regexp) logic
- Some other fixes and optimizations

##### 1.0.1 - 2015.07.31
- Some fixes for final MS Edge, replaced broken native `Reflect.defineProperty`
- Some minor fixes and optimizations
- Changed compression `client/*.min.js` options for safe `Function#name` and `Function#length`, should be fixed [#92](https://github.com/zloirock/core-js/issues/92)

##### 1.0.0 - 2015.07.22
- Added logic for [well-known symbols](https://github.com/zloirock/core-js/#ecmascript-6-regexp):
  - `Symbol.match`
  - `Symbol.replace`
  - `Symbol.split`
  - `Symbol.search`
- Actualized and optimized work with iterables:
  - Optimized  [`Map`, `Set`, `WeakMap`, `WeakSet` constructors](https://github.com/zloirock/core-js/#ecmascript-6-collections), [`Promise.all`, `Promise.race`](https://github.com/zloirock/core-js/#ecmascript-6-promise) for default `Array Iterator`
  - Optimized  [`Array.from`](https://github.com/zloirock/core-js/#ecmascript-6-array) for default `Array Iterator`
  - Added [`core.getIteratorMethod`](https://github.com/zloirock/core-js/#ecmascript-6-iterators) helper
- Uses enumerable properties in shimmed instances - collections, iterators, etc for optimize performance
- Added support native constructors to [`Reflect.construct`](https://github.com/zloirock/core-js/#ecmascript-6-reflect) with 2 arguments
- Added support native constructors to [`Function#bind`](https://github.com/zloirock/core-js/#ecmascript-5) shim with `new`
- Removed obsolete `.clear` methods native [`Weak`-collections](https://github.com/zloirock/core-js/#ecmascript-6-collections)
- Maximum modularity, reduced minimal custom build size, separated into submodules:
  - [`es6.reflect`](https://github.com/zloirock/core-js/#ecmascript-6-reflect)
  - [`es6.regexp`](https://github.com/zloirock/core-js/#ecmascript-6-regexp)
  - [`es6.math`](https://github.com/zloirock/core-js/#ecmascript-6-math)
  - [`es6.number`](https://github.com/zloirock/core-js/#ecmascript-6-number)
  - [`es7.object.to-array`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
  - [`core.object`](https://github.com/zloirock/core-js/#object)
  - [`core.string`](https://github.com/zloirock/core-js/#escaping-strings)
  - [`core.iter-helpers`](https://github.com/zloirock/core-js/#ecmascript-6-iterators)
  - Internal modules (`$`, `$.iter`, etc)
- Many other optimizations
- Final cleaning non-standard features
  - Moved `$for` to [separate library](https://github.com/zloirock/forof). This work for syntax - `for-of` loop and comprehensions
  - Moved `Date#{format, formatUTC}` to [separate library](https://github.com/zloirock/dtf). Standard way for this - `ECMA-402`
  - Removed `Math` methods from `Number.prototype`. Slight sugar for simple `Math` methods calling
  - Removed `{Array#, Array, Dict}.turn`
  - Removed `core.global`
- Uses `ToNumber` instead of `ToLength` in [`Number Iterator`](https://github.com/zloirock/core-js/#number-iterator), `Array.from(2.5)` will be `[0, 1, 2]` instead of `[0, 1]`
- Fixed [#85](https://github.com/zloirock/core-js/issues/85) - invalid `Promise` unhandled rejection message in nested `setTimeout`
- Fixed [#86](https://github.com/zloirock/core-js/issues/86) - support FF extensions
- Fixed [#89](https://github.com/zloirock/core-js/issues/89) - behavior `Number` constructor in strange case

##### 0.9.18 - 2015.06.17
- Removed `/` from [`RegExp.escape`](https://github.com/zloirock/core-js/#ecmascript-7-proposals) escaped characters

##### 0.9.17 - 2015.06.14
- Updated [`RegExp.escape`](https://github.com/zloirock/core-js/#ecmascript-7-proposals) to the [latest proposal](https://github.com/benjamingr/RexExp.escape)
- Fixed conflict with webpack dev server + IE buggy behavior

##### 0.9.16 - 2015.06.11
- More correct order resolving thenable in [`Promise`](https://github.com/zloirock/core-js/#ecmascript-6-promise) polyfill
- Uses polyfill instead of [buggy V8 `Promise`](https://github.com/zloirock/core-js/issues/78)

##### 0.9.15 - 2015.06.09
- [Collections](https://github.com/zloirock/core-js/#ecmascript-6-collections) from `library` version return wrapped native instances
- Fixed collections prototype methods in `library` version
- Optimized [`Math.hypot`](https://github.com/zloirock/core-js/#ecmascript-6-math)

##### 0.9.14 - 2015.06.04
- Updated [`Promise.resolve` behavior](https://esdiscuss.org/topic/fixing-promise-resolve)
- Added fallback for IE11 buggy `Object.getOwnPropertyNames` + iframe
- Some other fixes

##### 0.9.13 - 2015.05.25
- Added fallback for [`Symbol` polyfill](https://github.com/zloirock/core-js/#ecmascript-6-symbol) for old Android
- Some other fixes

##### 0.9.12 - 2015.05.24
- Different instances `core-js` should use / recognize the same symbols
- Some fixes

##### 0.9.11 - 2015.05.18
- Simplified [custom build](https://github.com/zloirock/core-js/#custom-build)
  - Added custom build js api
  - Added `grunt-cli` to `devDependencies` for `npm run grunt`
- Some fixes

##### 0.9.10 - 2015.05.16
- Wrapped `Function#toString` for correct work wrapped methods / constructors with methods similar to the [`lodash` `isNative`](https://github.com/lodash/lodash/issues/1197)
- Added proto versions of methods to export object in `default` version for consistency with `library` version

##### 0.9.9 - 2015.05.14
- Wrapped `Object#propertyIsEnumerable` for [`Symbol` polyfill](https://github.com/zloirock/core-js/#ecmascript-6-symbol)
- [Added proto versions of methods to `library` for ES7 bind syntax](https://github.com/zloirock/core-js/issues/65)
- Some other fixes

##### 0.9.8 - 2015.05.12
- Fixed [`Math.hypot`](https://github.com/zloirock/core-js/#ecmascript-6-math) with negative arguments
- Added `Object#toString.toString` as fallback for [`lodash` `isNative`](https://github.com/lodash/lodash/issues/1197)

##### 0.9.7 - 2015.05.07
- Added [support DOM collections](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice#Streamlining_cross-browser_behavior) to IE8- `Array#slice`

##### 0.9.6 - 2015.05.01
- Added [`String#lpad`, `String#rpad`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)

##### 0.9.5 - 2015.04.30
- Added cap for `Function#@@hasInstance`
- Some fixes and optimizations

##### 0.9.4 - 2015.04.27
- Fixed `RegExp` constructor

##### 0.9.3 - 2015.04.26
- Some fixes and optimizations

##### 0.9.2 - 2015.04.25
- More correct [`Promise`](https://github.com/zloirock/core-js/#ecmascript-6-promise) unhandled rejection tracking and resolving / rejection priority

##### 0.9.1 - 2015.04.25
- Fixed `__proto__`-based [`Promise`](https://github.com/zloirock/core-js/#ecmascript-6-promise) subclassing in some environments

##### 0.9.0 - 2015.04.24
- Added correct [symbols](https://github.com/zloirock/core-js/#ecmascript-6-symbol) descriptors
  - Fixed behavior `Object.{assign, create, defineProperty, defineProperties, getOwnPropertyDescriptor, getOwnPropertyDescriptors}` with symbols
  - Added [single entry points](https://github.com/zloirock/core-js/#commonjs) for `Object.{create, defineProperty, defineProperties}`
- Added [`Map#toJSON`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
- Removed non-standard methods `Object#[_]` and `Function#only` - they solves syntax problems, but now in compilers available arrows and ~~in near future will be available~~ [available](http://babeljs.io/blog/2015/05/14/function-bind/) [bind syntax](https://github.com/zenparsing/es-function-bind)
- Removed non-standard undocumented methods `Symbol.{pure, set}`
- Some fixes and internal changes

##### 0.8.4 - 2015.04.18
- Uses `webpack` instead of `browserify` for browser builds - more compression-friendly result

##### 0.8.3 - 2015.04.14
- Fixed `Array` statics with single entry points

##### 0.8.2 - 2015.04.13
- [`Math.fround`](https://github.com/zloirock/core-js/#ecmascript-6-math) now also works in IE9-
- Added [`Set#toJSON`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
- Some optimizations and fixes

##### 0.8.1 - 2015.04.03
- Fixed `Symbol.keyFor`

##### 0.8.0 - 2015.04.02
- Changed [CommonJS API](https://github.com/zloirock/core-js/#commonjs)
- Splitted and renamed some modules
- Added support ES3 environment (ES5 polyfill) to **all** default versions - size increases slightly (+ ~4kb w/o gzip), many issues disappear, if you don't need it - [simply include only required namespaces / features / modules](https://github.com/zloirock/core-js/#commonjs)
- Removed [abstract references](https://github.com/zenparsing/es-abstract-refs) support - proposal has been superseded =\
- [`$for.isIterable` -> `core.isIterable`, `$for.getIterator` -> `core.getIterator`](https://github.com/zloirock/core-js/#ecmascript-6-iterators), temporary available in old namespace
- Fixed iterators support in v8 `Promise.all` and `Promise.race`
- Many other fixes

##### 0.7.2 - 2015.03.09
- Some fixes

##### 0.7.1 - 2015.03.07
- Some fixes

##### 0.7.0 - 2015.03.06
- Rewritten and splitted into [CommonJS modules](https://github.com/zloirock/core-js/#commonjs)

##### 0.6.1 - 2015.02.24
- Fixed support [`Object.defineProperty`](https://github.com/zloirock/core-js/#ecmascript-5) with accessors on DOM elements on IE8

##### 0.6.0 - 2015.02.23
- Added support safe closing iteration - calling `iterator.return` on abort iteration, if it exists
- Added basic support [`Promise`](https://github.com/zloirock/core-js/#ecmascript-6-promise) unhandled rejection tracking in shim
- Added [`Object.getOwnPropertyDescriptors`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
- Removed `console` cap - creates too many problems
- Restructuring [namespaces](https://github.com/zloirock/core-js/#custom-build)
- Some fixes

##### 0.5.4 - 2015.02.15
- Some fixes

##### 0.5.3 - 2015.02.14
- Added [support binary and octal literals](https://github.com/zloirock/core-js/#ecmascript-6-number) to `Number` constructor
- Added [`Date#toISOString`](https://github.com/zloirock/core-js/#ecmascript-5)

##### 0.5.2 - 2015.02.10
- Some fixes

##### 0.5.1 - 2015.02.09
- Some fixes

##### 0.5.0 - 2015.02.08
- Systematization of modules
- Splitted [`es6` module](https://github.com/zloirock/core-js/#ecmascript-6)
- Splitted `console` module: `web.console` - only cap for missing methods, `core.log` - bound methods & additional features
- Added [`delay` method](https://github.com/zloirock/core-js/#delay)
- Some fixes

##### 0.4.10 - 2015.01.28
- [`Object.getOwnPropertySymbols`](https://github.com/zloirock/core-js/#ecmascript-6-symbol) polyfill returns array of wrapped keys

##### 0.4.9 - 2015.01.27
- FF20-24 fix

##### 0.4.8 - 2015.01.25
- Some [collections](https://github.com/zloirock/core-js/#ecmascript-6-collections) fixes

##### 0.4.7 - 2015.01.25
- Added support frozen objects as [collections](https://github.com/zloirock/core-js/#ecmascript-6-collections) keys

##### 0.4.6 - 2015.01.21
- Added [`Object.getOwnPropertySymbols`](https://github.com/zloirock/core-js/#ecmascript-6-symbol)
- Added [`NodeList.prototype[@@iterator]`](https://github.com/zloirock/core-js/#ecmascript-6-iterators)
- Added basic `@@species` logic - getter in native constructors
- Removed `Function#by`
- Some fixes

##### 0.4.5 - 2015.01.16
- Some fixes

##### 0.4.4 - 2015.01.11
- Enabled CSP support

##### 0.4.3 - 2015.01.10
- Added `Function` instances `name` property for IE9+

##### 0.4.2 - 2015.01.10
- `Object` static methods accept primitives
- `RegExp` constructor can alter flags (IE9+)
- Added `Array.prototype[Symbol.unscopables]`

##### 0.4.1 - 2015.01.05
- Some fixes

##### 0.4.0 - 2015.01.03
- Added [`es6.reflect`](https://github.com/zloirock/core-js/#ecmascript-6-reflect) module:
  - Added `Reflect.apply`
  - Added `Reflect.construct`
  - Added `Reflect.defineProperty`
  - Added `Reflect.deleteProperty`
  - Added `Reflect.enumerate`
  - Added `Reflect.get`
  - Added `Reflect.getOwnPropertyDescriptor`
  - Added `Reflect.getPrototypeOf`
  - Added `Reflect.has`
  - Added `Reflect.isExtensible`
  - Added `Reflect.preventExtensions`
  - Added `Reflect.set`
  - Added `Reflect.setPrototypeOf`
- `core-js` methods now can use external `Symbol.iterator` polyfill
- Some fixes

##### 0.3.3 - 2014.12.28
- [Console cap](https://github.com/zloirock/core-js/#console) excluded from node.js default builds

##### 0.3.2 - 2014.12.25
- Added cap for [ES5](https://github.com/zloirock/core-js/#ecmascript-5) freeze-family methods
- Fixed `console` bug

##### 0.3.1 - 2014.12.23
- Some fixes

##### 0.3.0 - 2014.12.23
- Optimize [`Map` & `Set`](https://github.com/zloirock/core-js/#ecmascript-6-collections):
  - Use entries chain on hash table
  - Fast & correct iteration
  - Iterators moved to [`es6`](https://github.com/zloirock/core-js/#ecmascript-6) and [`es6.collections`](https://github.com/zloirock/core-js/#ecmascript-6-collections) modules

##### 0.2.5 - 2014.12.20
- `console` no longer shortcut for `console.log` (compatibility problems)
- Some fixes

##### 0.2.4 - 2014.12.17
- Better compliance of ES6
- Added [`Math.fround`](https://github.com/zloirock/core-js/#ecmascript-6-math) (IE10+)
- Some fixes

##### 0.2.3 - 2014.12.15
- [Symbols](https://github.com/zloirock/core-js/#ecmascript-6-symbol):
  - Added option to disable addition setter to `Object.prototype` for Symbol polyfill:
    - Added `Symbol.useSimple`
    - Added `Symbol.useSetter`
  - Added cap for well-known Symbols:
    - Added `Symbol.hasInstance`
    - Added `Symbol.isConcatSpreadable`
    - Added `Symbol.match`
    - Added `Symbol.replace`
    - Added `Symbol.search`
    - Added `Symbol.species`
    - Added `Symbol.split`
    - Added `Symbol.toPrimitive`
    - Added `Symbol.unscopables`

##### 0.2.2 - 2014.12.13
- Added [`RegExp#flags`](https://github.com/zloirock/core-js/#ecmascript-6-regexp) ([December 2014 Draft Rev 29](http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts#december_6_2014_draft_rev_29))
- Added [`String.raw`](https://github.com/zloirock/core-js/#ecmascript-6-string)

##### 0.2.1 - 2014.12.12
- Repair converting -0 to +0 in [native collections](https://github.com/zloirock/core-js/#ecmascript-6-collections)

##### 0.2.0 - 2014.12.06
- Added [`es7.proposals`](https://github.com/zloirock/core-js/#ecmascript-7-proposals) and [`es7.abstract-refs`](https://github.com/zenparsing/es-abstract-refs) modules
- Added [`String#at`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
- Added real [`String Iterator`](https://github.com/zloirock/core-js/#ecmascript-6-iterators), older versions used Array Iterator
- Added abstract references support:
  - Added `Symbol.referenceGet`
  - Added `Symbol.referenceSet`
  - Added `Symbol.referenceDelete`
  - Added `Function#@@referenceGet`
  - Added `Map#@@referenceGet`
  - Added `Map#@@referenceSet`
  - Added `Map#@@referenceDelete`
  - Added `WeakMap#@@referenceGet`
  - Added `WeakMap#@@referenceSet`
  - Added `WeakMap#@@referenceDelete`
  - Added `Dict.{...methods}[@@referenceGet]`
- Removed deprecated `.contains` methods
- Some fixes

##### 0.1.5 - 2014.12.01
- Added [`Array#copyWithin`](https://github.com/zloirock/core-js/#ecmascript-6-array)
- Added [`String#codePointAt`](https://github.com/zloirock/core-js/#ecmascript-6-string)
- Added [`String.fromCodePoint`](https://github.com/zloirock/core-js/#ecmascript-6-string)

##### 0.1.4 - 2014.11.27
- Added [`Dict.mapPairs`](https://github.com/zloirock/core-js/#dict)

##### 0.1.3 - 2014.11.20
- [TC39 November meeting](https://github.com/rwaldron/tc39-notes/tree/master/es6/2014-11):
  - [`.contains` -> `.includes`](https://github.com/rwaldron/tc39-notes/blob/master/es6/2014-11/nov-18.md#51--44-arrayprototypecontains-and-stringprototypecontains)
    - `String#contains` -> [`String#includes`](https://github.com/zloirock/core-js/#ecmascript-6-string)
    - `Array#contains` -> [`Array#includes`](https://github.com/zloirock/core-js/#ecmascript-7-proposals)
    - `Dict.contains` -> [`Dict.includes`](https://github.com/zloirock/core-js/#dict)
  - [Removed `WeakMap#clear`](https://github.com/rwaldron/tc39-notes/blob/master/es6/2014-11/nov-19.md#412-should-weakmapweakset-have-a-clear-method-markm)
  - [Removed `WeakSet#clear`](https://github.com/rwaldron/tc39-notes/blob/master/es6/2014-11/nov-19.md#412-should-weakmapweakset-have-a-clear-method-markm)

##### 0.1.2 - 2014.11.19
- `Map` & `Set` bug fix

##### 0.1.1 - 2014.11.18
- Public release
