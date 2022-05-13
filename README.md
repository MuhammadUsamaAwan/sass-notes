# SASS

## Comments

```scss
/* Sass supports standard CSS comments */
// addition it supports inline comments
```

## Varaibles

```scss
$myFont: Helvetica, sans-serif;

body {
  font-family: $myFont;
}
```

## Nesting

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

## Partial Imports

### \_colors.scss

```scss
$myPink: #ee82ee;
$myBlue: #4169e1;
$myGreen: #8fbc8f;
```

### main.scss

```scss
//if you import the partial file, omit the underscore
@import 'colors';
```

## @mixin

```scss
// Defining mixins
@mixin important-text {
  color: red;
}
// using mixins
selector {
  @include mixin-name;
}

// using arguments
@mixin bordered($color, $width) {
  border: $width solid $color;
}

.myArticle {
  @include bordered(blue, 1px);
}

// Default argument
@mixin bordered($color: blue, $width: 1px) {
  border: $width solid $color;
}
```

## Media Query Using Mixins

```scss
@mixin for-size($size) {
  @if $size == phone-only {
    @media (max-width: 599px) {
      @content;
    }
  } @else if $size == tablet-portrait-up {
    @media (min-width: 600px) {
      @content;
    }
  } @else if $size == tablet-landscape-up {
    @media (min-width: 900px) {
      @content;
    }
  } @else if $size == desktop-up {
    @media (min-width: 1200px) {
      @content;
    }
  } @else if $size == big-desktop-up {
    @media (min-width: 1800px) {
      @content;
    }
  }
}

.header-title {
  font-size: 2rem;
  @include for-size(phone-only) {
    font-size: 1rem;
  }
}
```

## @extend

```scss
.button-basic {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report {
  @extend .button-basic;
  background-color: red;
}
```

## Conditional

```scss
@mixin triangle($size, $color, $direction) {
  height: 0;
  width: 0;

  border-color: transparent;
  border-style: solid;
  border-width: math.div($size, 2);

  @if $direction == up {
    border-bottom-color: $color;
  } @else if $direction == right {
    border-left-color: $color;
  } @else if $direction == down {
    border-top-color: $color;
  } @else if $direction == left {
    border-right-color: $color;
  } @else {
    @error "Unknown direction #{$direction}.";
  }
}
```

## Map Functions

```scss
$colors: (
  primary: #fff;,
);

selector {
  color: map-get(#colors, primary);
}
```

## Functions

```scss
$colors: (
  primary: #fff;,
);

@function color($color-name) {
  @return map-get($colors, $color-name);
}

selector {
  color: color(primary);
}
```

## Color Functions

```scss
mix(color1, color2, weight)
lighten(color, amount)
darken(color, amount)
saturate(color, amount)
desaturate(color, amount)
opacify(color, amount)
fade-in(color, amount)
transparentize(color, amount)
fade-out(color, amount)
```
