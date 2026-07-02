<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# zeroTo

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Return a new [ndarray][@stdlib/ndarray/ctor] filled with linearly spaced numeric elements which increment by `1` starting from zero along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.



<section class="usage">

## Usage

```javascript
import zeroTo from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-zero-to@deno/mod.js';
```

You can also import the following named exports from the package:

```javascript
import { assign } from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-zero-to@deno/mod.js';
```

#### zeroTo( shape\[, options] )

Returns a new [ndarray][@stdlib/ndarray/ctor] filled with linearly spaced numeric elements which increment by `1` starting from zero along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.

```javascript
var x = zeroTo( [ 2, 3 ] );
// returns <ndarray>[ [ 0.0, 1.0, 2.0 ], [ 0.0, 1.0, 2.0 ] ]
```

The function has the following parameters:

-   **shape**: array shape.
-   **options**: function options (_optional_).

The function accepts the following options:

-   **dims**: list of dimensions over which to perform operation. If not provided, the function generates values along the last dimension. Default: `[-1]`.
-   **dtype**: output [ndarray][@stdlib/ndarray/ctor] [data type][@stdlib/ndarray/dtypes]. Must be a numeric or "generic" [data type][@stdlib/ndarray/dtypes]. Default: `'float64'`.
-   **order**: specifies whether an [ndarray][@stdlib/ndarray/ctor] is `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **mode**: specifies how to handle indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **submode**: a mode array which specifies for each dimension how to handle subscripts which exceed array dimensions  (see [`ndarray`][@stdlib/ndarray/ctor]). If provided fewer modes than dimensions, the function recycles modes using modulo arithmetic. Default: `[ options.mode ]`.

By default, the function generates values along the last dimension of an output [ndarray][@stdlib/ndarray/ctor]. To perform the operation over specific dimensions, provide a `dims` option.

```javascript
var x = zeroTo( [ 2, 2 ], {
    'dims': [ 0, 1 ]
});
// returns <ndarray>[ [ 0.0, 1.0 ], [ 2.0, 3.0 ] ]
```

To specify the output [ndarray][@stdlib/ndarray/ctor] [data type][@stdlib/ndarray/dtypes], provide a `dtype` option.

```javascript
var x = zeroTo( [ 3 ], {
    'dtype': 'float32'
});
// returns <ndarray>[ 0.0, 1.0, 2.0 ]
```

#### zeroTo.assign( x\[, options] )

Fills an [ndarray][@stdlib/ndarray/ctor] with linearly spaced numeric elements which increment by `1` starting from zero along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.

```javascript
import zeros from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-zeros@deno/mod.js';

var x = zeros( [ 2, 3 ] );
// returns <ndarray>[ [ 0.0, 0.0, 0.0 ], [ 0.0, 0.0, 0.0 ] ]

var out = zeroTo.assign( x );
// returns <ndarray>[ [ 0.0, 1.0, 2.0 ], [ 0.0, 1.0, 2.0 ] ]

var bool = ( x === out );
// returns true
```

The function has the following parameters:

-   **x**: input [ndarray][@stdlib/ndarray/ctor]. Must have a numeric or "generic" [data type][@stdlib/ndarray/dtypes].
-   **options**: function options (_optional_).

The function accepts the following options:

-   **dims**: list of dimensions over which to perform operation. If not provided, the function generates values along the last dimension. Default: `[-1]`.

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   The function iterates over [ndarray][@stdlib/ndarray/ctor] elements according to the memory layout of the input [ndarray][@stdlib/ndarray/ctor]. Accordingly, performance degradation is possible when operating over multiple dimensions of a large non-contiguous multi-dimensional input [ndarray][@stdlib/ndarray/ctor]. In such scenarios, one may want to copy an input [ndarray][@stdlib/ndarray/ctor] to contiguous memory before performing the operation.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@deno/mod.js';
import zeroTo from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-zero-to@deno/mod.js';

// Create a new ndarray:
var x = zeroTo( [ 5, 5 ], {
    'dtype': 'generic'
});
console.log( ndarray2array( x ) );

// Generate values over a specific dimension:
x = zeroTo( [ 5, 5 ], {
    'dtype': 'generic',
    'dims': [ 0 ]
});
console.log( ndarray2array( x ) );

// Generate values over all dimensions:
x = zeroTo( [ 5, 5 ], {
    'dtype': 'generic',
    'dims': [ 0, 1 ]
});
console.log( ndarray2array( x ) );
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/blas-ext-zero-to.svg
[npm-url]: https://npmjs.org/package/@stdlib/blas-ext-zero-to

[test-image]: https://github.com/stdlib-js/blas-ext-zero-to/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/blas-ext-zero-to/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/blas-ext-zero-to/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/blas-ext-zero-to?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/blas-ext-zero-to.svg
[dependencies-url]: https://david-dm.org/stdlib-js/blas-ext-zero-to/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/blas-ext-zero-to/tree/deno
[deno-readme]: https://github.com/stdlib-js/blas-ext-zero-to/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/blas-ext-zero-to/tree/umd
[umd-readme]: https://github.com/stdlib-js/blas-ext-zero-to/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/blas-ext-zero-to/tree/esm
[esm-readme]: https://github.com/stdlib-js/blas-ext-zero-to/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/blas-ext-zero-to/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/blas-ext-zero-to/main/LICENSE

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor/tree/deno

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes/tree/deno

</section>

<!-- /.links -->
