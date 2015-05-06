# grunt-sst

> A simple Swig template generator.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-sst --save
```

This command will download the plugin package along with its dependencies, as well as add it as a dependency to your project's `package.json` file.

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-sst');
```

## The "sst" task

### Overview
In your project's Gruntfile, add a section named `sst` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  sst: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
});
```

### Options
The only specific configuration options the plugin may take are represented as an optional object representing Swig defaults.  You can merge custom Swig options with the Swig defaults by setting a `swigDefaults` property on the main options.  This approach is illustrated in the Custom Options section below.  The Swig defaults are documented on [the repository page for Swig itself](http://paularmstrong.github.io/swig/docs/api/#SwigOpts).  The most notable of the Swig defaults that may often be set when using this plugin is the `locals` object, which allows you to pass global data to all templates.  The `locals` object is created by referencing a JSON file by path in the plugin options.  Again, this is illustrated below.

### Usage Examples

#### Default Options
In this example, the plugin uses Grunt's native file expansion to recursively search for `.swig` files in a specific current working directory.  Those files are then rendered with Swig into a specified destination and with a specified file extension of `.html`.

```js
grunt.initConfig({
  sst: {
    options: {},
    files: {[
        expand: true,
        cwd: 'foo',
        dest: 'your/compiled/assets',
        src: [
            '**/*/swig'
        ],
        ext: '.html'
    ]},
  },
});
```

#### Custom Options
In this example, custom options are used to do something else with whatever else. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result in this case would be `Testing: 1 2 3 !!!`

```js
grunt.initConfig({
  sst: {
    options: {
      separator: ': ',
      punctuation: ' !!!',
    },
    files: {
      'dest/default_options': ['src/testing', 'src/123'],
    },
  },
});
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_(Nothing yet)_
