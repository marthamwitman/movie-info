# movie-info 
[![bitHound Code](https://www.bithound.io/github/lacymorrow/movie-info/badges/code.svg)](https://www.bithound.io/github/lacymorrow/movie-info) [![npm version](https://badge.fury.io/js/movie-info.svg)](https://badge.fury.io/js/movie-info) [![Build Status](https://travis-ci.org/lacymorrow/movie-info.svg?branch=master)](https://travis-ci.org/lacymorrow/movie-info) [![Try movie-info on RunKit](https://badge.runkitcdn.com/movie-info.svg)](https://npm.runkit.com/movie-info)

> Fetch information, images, rating, description, etc. about a movie.

[![movie-info](https://github.com/lacymorrow/movie-info/raw/master/demo.svg?sanitize=true)](https://github.com/lacymorrow/movie-info)

#### [Try it on RunKit](https://runkit.com/lacymorrow/movie-info) ([_Output_](https://movie-info-kdbpuifpuxt8.runkit.sh/?name=Oceans+Eleven))


## Features
 * Use anywhere, browser or Node - UMD ([CanIUse](https://caniuse.com/#feat=fetch))
 * Promise and Callback API
 * Finds:
   * Title
   * Release Date
   * Poster and backdrop images
   * IMDB rating + vote count
   * Recent popularity rating
   * Adult film (boolean)


## Install

```bash
// From the command line
$ npm install -g movie-info
```

```html
// Globally in the browser (Cloudflare CDN)
<script type="text/javascript" src="https://unpkg.com/movie-info" />
```


#### From the command line

```bash
$ movie-info --help

Usage
  $ movie-info movie [year]

Example
  $ movie-info 'Oceans Eleven' 1960  
  //=> { ... }
```



## Usage

```bash
$ npm install --save movie-info
```

```js

const movieInfo = require('movie-info')

// Callbacks
movieInfo('Avatar', function (err, res){
    if (err) return err;
    console.log(res)
    //=> { ... }
})

// Promises
movieInfo('Avatar').then(console.log)

// or, search with year and handle output
movieInfo('Oceans Eleven', '1960').then(
    function (res) {
        // success
        console.log(res)
        //=> { ... }
    },
    function (err) {
        // failed
    }
})

// error handling
movieInfo('Avatar').catch(error => {
    // respond to error
});

```

##### Response

```js
{
    adult: false,
    backdrop_path: '/lhkU86q5cszZkca9MVQLMvUAE6m.jpg',
    id: 1640,
    original_title: 'Crash',
    release_date: '2004-09-10',
    poster_path: '/pG8LL4LYMCr5uikhx9rewrW8352.jpg',
    popularity: 3.30511799781063,
    title: 'Crash',
    vote_average: 6.9,
    vote_count: 271,
    image_base: 'http://image.tmdb.org/t/p/original'
}
```

##### Images

Combine the `image_base` with the desired path to create a complete image URL.

```js
var imageUrl = response.image_base + response.poster_path
    //=> http://image.tmdb.org/t/p/original/pG8LL4LYMCr5uikhx9rewrW8352.jpg
```


## API

### movieInfo(movie [, year ] [, callback])

Returns a Promise which resolves to a movie object. 

#### movie

*Required*  
Type: `string`

Movie title to search for.

#### year 

Type: `string`

Movie release year to search for. _(optional)_

#### callback (error, result)

type: `function`

Callback function. _(optional)_


## Related

* [album-art](https://github.com/lacymorrow/album-art)
* [movie-art](https://github.com/lacymorrow/movie-art)
* [movie-trailer](https://github.com/lacymorrow/movie-trailer)


## License

This package uses data from TMDB. You may consult [TMDB terms of service](https://www.themoviedb.org/documentation/api/terms-of-use) for usage rights.

[MIT](http://opensource.org/licenses/MIT) © [Lacy Morrow](http://lacymorrow.com)
