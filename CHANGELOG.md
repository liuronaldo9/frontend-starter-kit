# 18.0

#### :nail_care: Refactor
* `core/static_src/sass` :arrow_forward: [Springload Starter Styles](springload/frontend-starter-styles) repo!
* `core/static_src/images` :arrow_forward:  :wastebasket: 
* `core/static_src/svg` :arrow_forward:  :wastebasket:
* `core/static_src/js` :arrow_forward:  ...the following table

| Before          | After           |
|-----------------|-----------------|
| `polyfills.js`  | |
| *Promise polyfill* | Nothing! Modern browsers have Promise already so the need for this is reduced. IE11 doesn't support Promises but use [`bluebird`](https://www.npmjs.com/package/bluebird). |
| *Object.assign polyfill* |  The `object.assign` polyfill can be replaced by Babel features. |
| `format.js`       | |
| *Date formatting* | Prefer [`Intl`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl) available in modern browsers and IE11, or [`date-fns`](https://github.com/date-fns/date-fns) if necessary |
| *padNumber*      | Use lodash's pad functions. |
| *humanNumber*    | Use [`Number.toLocalString`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString) noting the Intl arguments and older Safari compat problems |
| `keycodes.js`    | Use [`keycode-js`](https://www.npmjs.com/package/keycode-js) |
| `interface.js`   | Nothing! Browser detection code and constants for `NBSP` as unicode are things you can find online |
| `analytics.js`   | Uh... I'm not sure what on earth this is doing :arrow_forward: :wastebasket: in the meantime |
| `/components/*`   | :arrow_forward: :wastebasket: |


#### :bug: Bug Fix
* 
#### :memo: Documentation
* 
#### :house: Internal
* 


# 1.0 before 2018

#### :bug: Bug Fix
* 
#### :nail_care: Enhancement
* 
#### :memo: Documentation
* 
#### :house: Internal
* 