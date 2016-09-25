# Grip CSS grid system

**Superclean, powerful, responsive, Sass-based, BEM-syntax CSS grid system based on the incredible [Avalanche](https://github.com/colourgarden/avalanche) grid system.**


## Why use Avalanche?

- No bloat. Only create the selectors you'll actually use
- No duplication. 1/2 == 2/4 so why create two selectors?
- No floats. No clears. No .last
- Flexible, configurable naming conventions
- Nesting to infinity and beyond
- Integrated media query mixin. Connect your media queries to your grid breakpoints


## So, why Grip then?

- It's strict BEM. Our selectors may be uglier but that's a good thing
- It's mobile-first. Width modifiers modify a cell at a given, named breakpoint


## Demo

Coming Soon!


## Installation

1. Import `_grip.scss` to your project via Bower, NPM, RubyGems or manually copying to vendor folder (`@import "vendor/grip"`)
2. Override settings to fit your requirements or use the defaults
3. Compile!

### Bower

`bower install --save grip-grid`

### NPM

`npm install --save grip-grid`

### RubyGems

`gem install grip-grid-rails`

### Rails via Bundler

In your `Gemfile`:

`gem 'grip-grid-rails'`

And in your application manifest:

`@import 'grip';`


## Usage

Example of a two column, responsive, centered grid. All grid layout classes and responsive width classes are modifiers.

```
<div class="grid grid--center">
  <div class="grid__cell grid__cell--25 grid__cell--50-at-medium"></div>
  <div class="grid__cell grid__cell--25 grid__cell--50-at-medium"></div>
  <div class="grid__cell grid__cell--25 grid__cell--50-at-medium"></div>
  <div class="grid__cell grid__cell--25 grid__cell--50-at-medium"></div>
</div>
```


## Settings

**`$grip-namespace`**
Global prefix for layout and cell class names. Default: `grid`.

**`$grip-gutter`**
Gutter width between cells. Default: `16px`.

**`$grip-width-class-style`**
Naming style of width classes. Default: `'percentage'`. Options:
- `percentage` (grid__cell--25, grid__cell--50 etc)
- `fraction` (grid__cell--1/2, grid__cell--3/4 etc)
- `fragment` (grid__cell--1-of-3, grid__cell--4-of-5 etc).

**`$grip-widths`**
Sass list of width denominator values (when expressed as a fraction). For example, based on the class style:
- `2` produces:
    + as percentage: `grid__cell--50`
    + as fraction: `grid__cell--1/2`
    + as fragment: `grid__cell--1-of-2`
- `3` produces:
    + as percentage: `grid__cell--33` and `grid__cell--66`
    + as fraction:  `grid__cell--1/3` and `grid__cell--1/2`
    + as fragment:  `grid__cell--1-of-3` and `grid__cell--2-of-3`
- etc.
Default: `( 2, 3, 4 )`.
*N.B. This setting has a large impact on the size of your compiled CSS. Avoid bloat by inputting just the numbers you'll use.*

**`$grip-enable-responsive`**
Enable/disable the inclusion of responsive width classes. With this enabled, class names (for denominators set above) will be created for each of your breakpoint aliases (set below). Default: `true`.

**`$grip-breakpoints`**
Sass map of responsive breakpoint aliases and associated media queries (in key-value pairs).
*N.B. This setting has a large impact on the size of your compiled CSS. Avoid bloat by inputting just the breakpoints you'll use.*
Default:
```
(
  "medium":  "screen and (min-width: 760px)",
  "wide":    "screen and (min-width: 960px)",
  "x-wide":  "screen and (min-width: 1160px)",
)
```


## Grid layouts

### `grid` Block Modifiers

Apply as modifier classes to your base `grid` element. For example; `<div class="grid grid--center">`.

All optionable grid layouts listed below are switched off by default. Set to `true` to enable.

**`$grip-enable-grid-center`**
All cells are horizontally centered within the container.

**`$grip-enable-grid-right`**
All cells are horizontally aligned to the right within the container.

**`$grip-enable-grid-middle`**
All cells are vertically centered within in the container.

**`$grip-enable-grid-bottom`**
All cells are vertically aligned to the bottom of the container.

**`$grip-enable-grid-flush`**
Gutters removed between cells.

**`$grip-enable-grid-tiny`**
Gutters between cells set to a quarter of the global gutter value. Default: `4px`.

**`$grip-enable-grid-small`**
Gutters between cells set to half of the global gutter value. Default: `8px`.

**`$grip-enable-grid-large`**
Gutters between cells set to double the global gutter value. Default: `32px`.

**`$grip-enable-grid-huge`**
Gutters between cells set to quadruple the global gutter value. Default: `64px`.

**`$grip-enable-grid-auto`**
All cells take up an unspecified width set by their content.

**`$grip-enable-grid-rev`**
Grid cells are displayed in the opposite of their source order.

### `grid__cell` Element Modifiers

**`$grip-enable-grid-cell-center`**
Center an individual grid cell within the container. For example; `<div class="grid__cell grid__cell--center">`.

**`$grip-enable-grid-cell-content-center`**
Centers the immediate child of the cell by displaying it as `inline-block`. For example; `<div class="grid__cell grid__cell--content-center">`

**`$grip-enable-grid-cell-content-right`**
Aligns the immediate child of the cell to the right by displaying it as `inline-block`. For example; `<div class="grid__cell grid__cell--content-right">`


## Browser support

All modern browsers are supported and Internet Explorer from IE9 upwards. If IE8 support is required then all that is needed is a pixel-value to be set for `font-size` on `.grid__cell`. This is due to IE8 not supporting rem units. If you need to support IE8 then you should use something like [gulp-pxrem](https://github.com/nnn-li/gulp-pxrem) in your build step.


## Questions

If you have any questions or need some help then feel free to [open an issue](https://github.com/meowsus/grip/issues/new).


## Special Thanks

- [Tom Hare](https://github.com/colourgarden) for creating a truly great piece of software.
