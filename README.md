# css-to-react-native-transform

[![NPM version](http://img.shields.io/npm/v/css-to-react-native-transform.svg)](https://www.npmjs.org/package/css-to-react-native-transform)
[![Build Status](https://travis-ci.org/kristerkari/css-to-react-native-transform.svg?branch=master)](https://travis-ci.org/kristerkari/css-to-react-native-transform)
[![Build status](https://ci.appveyor.com/api/projects/status/75s8ls2m47by8b1x/branch/master?svg=true)](https://ci.appveyor.com/project/kristerkari/css-to-react-native-transform/branch/master)

A lightweight wrapper on top of
[css-to-react-native](https://github.com/styled-components/css-to-react-native)
to allow valid CSS to be turned into React Native Stylesheet objects.

Example:

```css
.myClass {
  font-size: 18px;
  line-height: 24px;
  color: red;
}

.other {
  padding: 1rem;
}
```

is transformed to:

```js
{
  myClass: {
    fontSize: 18,
    lineHeight: 24,
    color: "red"
  },
  other: {
    paddingBottom: 16,
    paddingLeft: 16,
    paddingRight: 16,
    paddingTop: 16
  }
}
```

## API

```js
import transform from "css-to-react-native-transform";
// or const transform = require("css-to-react-native-transform").default;

transform(`
  .foo {
    color: #f00;
  }
`); // => { foo: { color: "#f00" } }
```

## Limitations

* For `rem` unit the root element `font-size` is currently set to 16 pixels. A
  setting needs to be implemented to allow the user to define the root element
  `font-size`.
* There is also support for the `box-shadow` shorthand, and this converts into
  `shadow-` properties. Note that these only work on iOS.
