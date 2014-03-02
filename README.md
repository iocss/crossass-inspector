# Crossass Inspector

A Sass mixin / function library for better variable inspection in development.

![Crossass Inspector](http://raw.github.com/whizark/crossass-inspector/master/crossass-inspector.png)

## Requirement

* [Sass](http://sass-lang.com/) 3.3.0+

## Installation

```sh
bower install crossass-inspector
```

or just copy ```crossass-inspector``` folder into your project.

## Usage

### Import

```scss
// For development environment
@import 'bower_components/crossass-inspector/scss/environment/development';

// For production environment
//@import 'bower_components/crossass-inspector/scss/environment/production';

@import 'bower_components/crossass-inspector/scss/inspector';
```

or

```scss
// For development environment
@import 'your-folder/crossass-inspector/scss/environment/development';

// For development environment
// @import 'your-folder/crossass-inspector/scss/environment/production';

@import 'your-folder/crossass-inspector/scss/inspector';
```

### Inspection

```scss
$variable: (
    number                : 1,
    string                : 'string',
    bool                  : true,
    color                 : white,
    'null'                : null,
    space-separated-list  : (1 2 3),
    comma-separated-list  : (1, 2, 3),
    list-in-list          : (1 (a b c) ),
    map                   : (a: 1, b: 2, c: 3),
    list-in-map           : (a: (1 2 3) ),
    map-in-map            : (A: (a: 1, b: 2, c: 3) )
);

.inspection {
    @include x-inspect($variable);
}
```

Compiling with Sass, it outputs debug information.

```
DEBUG: (map) (
DEBUG:     number: (number) 1
DEBUG:     string: (string) string
DEBUG:     bool: (bool) true
DEBUG:     color: (color) white
DEBUG:     null: (null)
DEBUG:     space-separated-list: (list) (
DEBUG:         (number) 1
DEBUG:         (number) 2
DEBUG:         (number) 3
DEBUG:     )
DEBUG:     comma-separated-list: (list) (
DEBUG:         (number) 1
DEBUG:         (number) 2
DEBUG:         (number) 3
DEBUG:     )
DEBUG:     list-in-list: (list) (
DEBUG:         (number) 1
DEBUG:         (list) (
DEBUG:             (string) a
DEBUG:             (string) b
DEBUG:             (string) c
DEBUG:         )
DEBUG:     )
DEBUG:     map: (map) (
DEBUG:         a: (number) 1
DEBUG:         b: (number) 2
DEBUG:         c: (number) 3
DEBUG:     )
DEBUG:     list-in-map: (map) (
DEBUG:         a: (list) (
DEBUG:             (number) 1
DEBUG:             (number) 2
DEBUG:             (number) 3
DEBUG:         )
DEBUG:     )
DEBUG:     map-in-map: (map) (
DEBUG:         A: (map) (
DEBUG:             a: (number) 1
DEBUG:             b: (number) 2
DEBUG:             c: (number) 3
DEBUG:         )
DEBUG:     )
DEBUG: )
```

## Variables

Variable | Type | Description
--- | --- | ---
$x-inspector-environment | String | The environment string
$x-inspector-debug | Bool | Whether output debug information using ```@debug```
$x-inspector-toolbar | Bool | Whether show toolbar on screen
$x-inspector-toolbar-position | String | The toolbar position (```top``` | ```bottom```)
$x-inspector-indent-size | Number | The indent size (space) for the variable inspection

## Environment

### Development

Variable | Default value
--- | ---
$x-inspector-environment | 'development'
$x-inspector-debug | true
$x-inspector-toolbar | true
$x-inspector-toolbar-position | 'bottom'
$x-inspector-indent-size | 4

### Production

Variable | Default value
--- | ---
$x-inspector-environment | 'production'
$x-inspector-debug | false
$x-inspector-toolbar | false
$x-inspector-toolbar-position | 'bottom'
$x-inspector-indent-size | 4
