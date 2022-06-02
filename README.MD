# Forked Branch Package Details

This branch has update for minIntegerLen Prop, which sets length of default digits in number. This is react-odometer.js patch to support odometer.js patch for length posted by [mikaelhm pull request/repo](https://github.com/mikaelhm/odometer).

## How To install this branch

```bash
npm i sushantgwr87/react-odometerjs
```
## Things to do after installation
This package will also install current version(not updated or unfixed) of [Odometer.js](https://github.com/HubSpot/odometer) which indeed will throw errors.

To fix it, just replace all files from ```projectfolder/node-modules/odometer``` with the files from [mikaelhm pull request/repo](https://github.com/mikaelhm/odometer)

After this navigate to odometer in node-modules and remove **jquery** from following files code - odometer.js, odometer.coffee and odometer.min.js.
### Demo
#### File - odometer.js
#### Original Code
Find it at the end of code or last lines/paragraph of code in all 3 files
```javascript
if (typeof define === 'function' && define.amd) {
    define(["jquery"], function() {
      return Odometer;
    });
  } else if (typeof exports !== "undefined" && exports !== null) {
    module.exports = Odometer;
  } else {
    window.Odometer = Odometer;
  }

}).call(this);
```
#### Changed Code 
```javascript
if (typeof define === 'function' && define.amd) {
    define([], function() {
      return Odometer;
    });
  } else if (typeof exports !== "undefined" && exports !== null) {
    module.exports = Odometer;
  } else {
    window.Odometer = Odometer;
  }

}).call(this);
```

Only remove the string from define function and keep the empty array as paramter in all files.

After this changed you can use the minIntegerLen as prop in component and it will work.
**Example**
```javascript
<Odometer format="d" minIntegerLen={3} duration={1000} value={5000} /> 
```

## Update or Release as actual patch
Can't be done until original package is updated but will think of to release my own package once I get hold on all working of npm and scripts.

# About React Odometer.js (orginal package)

Simple React wrapper around [Odometer.js](https://github.com/HubSpot/odometer).

## How to use it

1. Installation

```bash
npm install --save react-odometerjs
```

or

```bash
yarn add react-odometerjs
```

2. Include component in your application:

```javascript
import Odometer from 'react-odometerjs';
// ...
return <Odometer value={1234} format="(.ddd),dd" />;
```

> Don't forget to include styles on your page. Official themes can be found
> [here](http://github.hubspot.com/odometer/api/themes/).

## Options

You can pass odometer __options via props__. See
[official documentation](http://github.hubspot.com/odometer/) of Odometer.js to learn about
available options.

## [Next.js](https://github.com/zeit/next.js/) integration

Because Odometer.js requires `document` object, we should load library using
[dynamic import](https://github.com/zeit/next.js/#dynamic-import), to avoid loading library on
server-side.

Example snippet:

```javascript
import dynamic from 'next/dynamic'

const Odometer = dynamic(import('react-odometerjs'), {
    ssr: false,
    loading: () => 0
});
// ...
return <Odometer value={1234} format="(.ddd),dd" />;
```

## Gatsby

`Odometer.js`
```js
import Odometer from 'react-odometerjs'
export default Odometer
```

`App.js`
```js
import loadable from '@loadable/component'

const Odometer = loadable(() => import('./Odometer'))

...

<Odometer value={1234} />
```

## Issues

Found an issue? You are welcome [here](https://github.com/inferusvv/react-odometerjs/issues).
