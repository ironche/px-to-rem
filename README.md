# px-to-rem sass function

Function `px-to-rem` provides px to rem unit conversion to help develop interfaces where usage of rem units is needed.

## Usage

### Syntax

**px-to-rem**( *valueList* [, *baseSize*] )

### Parameters

- valueList (required): A standard sass space separated list of values in px unit. All units are going to be stripped, so whatever is passed as argument, it will be treated as px unit.
- baseSize (optional): If specified, it will be used to alter the default proportion of `1rem=16px`. The default value for this argument is 16.

### Example

SCSS input
```scss
.test {
  position: relative;

  // All units are going to be stripped, as it is assumed that px are used
  margin: px-to-rem(16px 20 24rem 32%);

  // Single value is also permitted
  border: px-to-rem(2) solid black;

  // Variables may be passed
  $gutter: 40px 44px 100px;
  padding: px-to-rem($gutter);
  
  // When base size is different from 16px
  top: px-to-rem(320, 10);

  /*
    Neither of the following are allowed

    right: px-to-rem(());          // empty list
    bottom: px-to-rem();           // no arguments
    left: px-to-rem([40px, 50px]); // comma separated list
  */
}
```

CSS output
```css
.test {
  position: relative;
  margin: 1rem 1.25rem 1.5rem 2rem;
  border: 0.125rem solid black;
  padding: 2.5rem 2.75rem 6.25rem;
  top: 32rem;
}
```

## Development notes

[NodeJS](https://nodejs.org) and [npm](https://www.npmjs.com) are required, along with [node-sass](https://github.com/sass/node-sass) library. To fire up dev script, execute `npm install` and then `npm start` in the console.

## Credits and inspiration

- `strip-unit` sass function by [Hugo Giraudel](https://css-tricks.com/snippets/sass/strip-unit-function)
- inspired by the article from [Chris Coyier](https://css-tricks.com/snippets/css/less-mixin-for-rem-font-sizing)

## Release notes

| Version | Description |
| ------- | ----------- |
| 1.0.0 | Initial version |
