# grunt-tfs-unlock

[![npm version](https://badge.fury.io/js/grunt-tfs-unlock.svg)](http://badge.fury.io/js/grunt-tfs-unlock)
[![Dependencies Status](https://david-dm.org/danactive/grunt-tfs-unlock.svg)](https://david-dm.org/danactive/grunt-tfs-unlock)
[![DevDependencies Status](https://david-dm.org/danactive/grunt-tfs-unlock/dev-status.svg)](https://david-dm.org/danactive/grunt-tfs-unlock#info=devDependencies)
[![MIT Licensed](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](http://opensource.org/licenses/MIT)

> Checkout Windows TFS locked files with Team Foundation Server

## Getting Started

```shell
npm install grunt-tfs-unlock --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-tfs-unlock');
```

## The "tfs-unlock" task

### Overview
In your project's Gruntfile, add a section named `tfs-unlock` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  tfs-unlock: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

### Options

#### options.action
Type: `String`
Default value: `checkout`

The TFS command applied to the target files.  Checkout or undo are currently supported

#### options.tfsPath
Type: `String` || `Array of Strings`

Todo: Improve enumeration, but for now pass a Windows shell path to parent location of `tf.exe`.  String path the Visual Studio folder, or use the enumerated array.  First index is Visual Studio version number vs2008, vs2010, vs2012, vs2013.  Second index is software bit bit32, or bit64.

#### options.wait
Type: `Number`
Default value: 3

Set the sleep duration for the TFS command to finish its work.

### Usage Examples

#### Visual Studio 2010 64-bit Options

```js
grunt.initConfig({
	"tfs-unlock": {
		checkout: {
			options: {
				tfsPath: ["vs2010", "bit64"], // optional
				action: 'checkout'
			},
			files: {
				src: []
			}
		},
		undo: {
			options: {
				tfsPath: ["vs2010", "bit64"],
				action: 'undo'
			},
			files: {
				src: []
			}
		}
	}
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
 * 2016-05-15   v0.4.0   Update dependencies and dev-dependencies
 * 2015-03-11   v0.3.2   Improve error catching
 * 2015-03-11   v0.3.1   tfsPath is optional
 * 2015-02-16   v0.3.0   Update tfs-unlock dependency to v.0.3.x
 * 2015-01-24   v0.2.0   Update tfs-unlock dependency to v.0.2.0
 * 2013-06-02   v0.1.2   Add sleep for TFS to complete command
 * 2013-06-02   v0.1.1   Fix dependencies
 * 2013-06-02   v0.1.0   First stable release to npm