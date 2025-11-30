# karma-lodash-template-preprocessor

[Karma](http://karma-runner.github.com) preprocessor to compile
[Lo-Dash templates](http://lodash.com/docs#template) on the fly.

## Deprecation notice

See [karma-runner/karma](https://github.com/karma-runner/karma?tab=readme-ov-file#karma-is-deprecated-and-is-not-accepting-new-features-or-general-bug-fixes):

> Based on the current state of the web testing ecosystem, we have made the hard decision to deprecate Karma. \[...]
>
> For those outside Angular looking to migrate off Karma, both [Web Test Runner](https://modern-web.dev/docs/test-runner/overview/) and [`jasmine-browser-runner`](https://github.com/jasmine/jasmine-browser-runner) provide browser-based unit testing solutions which can be used as a direct alternative. [Jest](https://jestjs.io/) and [Vitest](https://vitest.dev/) also provide Node-based alternatives.

## Installation

```bash
npm install karma-lodash-template-preprocessor --save-dev
```

## Configuration

Following code shows all configuration options:

```js
// karma.conf.js
module.exports = function( config ) {
  config.set({
    preprocessors: {
      "**/*.template.js": [ "lodash" ]
    },

    lodashPreprocessor: {
      // Template data. You can use function, which returns object
      // When omitted, templates are compiled into functions that take data
      // arguments.
      data: {
        "this will be passed": "to _.template as second argument"
      },

      // Name of global namespace object that template functions are attached
      // to. Only useful in conjunction with compiled function (i.e. when no
      // data object is defined).
      globalVariable: 'JST'

      // Options set as _.templateSettings
      options: {
        interpolate: /regexp/,
        variable: "info"
        // Full list: http://lodash.com/docs#template
      },

      // Filename transform function ("file.template.js" > "file.js"):
      transformPath: function( path ) {
        return path.replace( /\.template\./i, "." );
      }
    }
  });
};
```
