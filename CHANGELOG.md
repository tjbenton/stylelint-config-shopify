# Changelog

## [Unreleased]

- Relaxed the stylelint peer dependency version range to allow `8.2.x` in projects consuming this config ([#25](https://github.com/Shopify/stylelint-config-shopify/pull/25))

## [4.0.0] - 2017-11-17

- Replaces [`prettier-stylelint`](https://github.com/hugomrdias/prettier-stylelint) with a [forked](https://github.com/ismail-syed/prettier-stylelint-formatter) version addressing an [issue](https://github.com/hugomrdias/prettier-stylelint/issues/3) [#23](https://github.com/Shopify/stylelint-config-shopify/pull/23)

### Migration Suggestions
- If `stylelint-config-shopify/prettier` is used, please replace `prettier-stylelint` with `prettier-stylelint-formatter`.

    ```
    yarn remove prettier-stylelint && yarn add prettier-stylelint-formatter
    ```

## [3.0.2] - 2017-11-14

* `declaration-block-no-redundant-longhand-properties` now allows longhand `grid` properties, see [#21](https://github.com/Shopify/stylelint-config-shopify/pull/21)

## [3.0.1] - 2017-11-13

- Removed `position: fixed` from the property value blacklist, see [#18](https://github.com/Shopify/stylelint-config-shopify/pull/18)
- Allowed digits in class selector names (e.g. `.rotate180`), see [#17](https://github.com/Shopify/stylelint-config-shopify/pull/17)
- Enforce property grouping, see [#10](https://github.com/Shopify/stylelint-config-shopify/pull/10)
- Turn off `order/order` [#19](https://github.com/Shopify/stylelint-config-shopify/pull/19)

### tl;dr

- Put variables & custom properties at the top (unless anyone feels strongly about this)
- Then come weird props, positioning & box model properties
- All other properties come after
- No specific property order is enforced

### The following patterns are _not_ considered warnings:

```scss
.Foo {
  $foo: 'foo';
  position: relative;
  display: block;
  margin: 10px;
  color: $foo;
}

.Foo {
  $foo: 'foo';
  position: relative;
  margin: 10px;
  display: block;
  color: $foo;
}
```

### The following patterns are considered warnings:

```scss
.Foo {
  position: relative;
  display: block;
  $foo: 'foo';
  color: $foo;
}

.Foo {
  $foo: 'foo';
  color: $foo;
  position: relative;
  display: block;
}
```


## [2.1.0] - 2017-08-25

### Updated
* [stylelint-scss](https://github.com/kristerkari/stylelint-scss) from `1.4.x` to `^2.0.1`
* Replaced deprecated `scss/at-mixin-no-argumentless-call-parentheses` rule with its equivalent `scss/at-mixin-argumentless-call-parentheses`
* `eslint-plugin-shopify` to the latest version, and updated ESLint to the appropriate version

### Changed
* `media-feature-name-no-unknown` to ignore `prefers-reduced-motion`

## [2.0.1] - 2017-07-28

### Changed
* Set `selector-max-type` to 1

## [2.0.0] - 2017-07-27

### Added

* New plugin:
  * Added `stylelint-order` which replaces `declaration-block-properties-order`

* New rules:
  * `rule-empty-line-before`
  * `selector-max-universal`
  * `at-rule-semicolon-space-before`
  * `selector-max-attribute`
  * `selector-max-class`
  * `selector-max-combinators`
  * `selector-max-id`
  * `selector-max-type`
  * `function-url-scheme-blacklist` (disabled)
  * `media-feature-name-whitelist` (disabled)
  * `time-min-milliseconds` (disabled)

### Removed

* Deprecated rules:
  * `block-no-single-line`
  * `no-indistinguishable-colors`
  * `declaration-block-no-ignored-properties`
  * `declaration-block-properties-order`
  * `function-url-data-uris`
  * `no-browser-hacks`
  * `no-unsupported-browser-features`
  * `media-feature-no-missing-punctuation`
  * `custom-property-no-outside-root`
  * `root-no-standard-properties`
  * `rule-nested-empty-line-before`
  * `rule-non-nested-empty-line-before`


### Changed

* Properties order for shorthand notation with margin, padding, border styles have been updated to follow:
```
property: <top> <right> <bottom> <left>
```

## 1.0.0 - 2017-05-29
* Initial release


[Unreleased]: https://github.com/Shopify/stylelint-config-shopify/compare/v4.0.0...HEAD
[4.0.0]: https://github.com/Shopify/stylelint-config-shopify/compare/v3.0.2...v4.0.0
[3.0.2]: https://github.com/Shopify/stylelint-config-shopify/compare/v3.0.1...v3.0.2
[3.0.1]: https://github.com/Shopify/stylelint-config-shopify/compare/v2.1.0...v3.0.1
[2.1.0]: https://github.com/Shopify/stylelint-config-shopify/compare/v2.0.1...v2.1.0
[2.0.1]: https://github.com/Shopify/stylelint-config-shopify/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/Shopify/stylelint-config-shopify/compare/v1.0.0...v2.0.0
