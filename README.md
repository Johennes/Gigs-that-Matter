jquery.lastfm
=============

A jQuery plugin for convenient access to the Last.fm API

Check out the demo: [click](http://htmlpreview.github.io/?https://github.com/Johennes/jquery.lastfm/blob/master/demo/index.html)

# Usage

To create a new API access object, use the following code

```javascript
var lastfm = new $.lastfmAPI('XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
```

where `'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'` is your Last.fm API key.
Afterwards you can invoke a number of functions on the access object
which are discussed in detail below.

## Getting User Information

To acquire information about a Last.fm user you can use the
`getUserInfo` function

```javascript
lastfm.getUserInfo(user, callback);
```

with the parameters:

* `user` - The Last.fm username
* `callback` - A callback function with a single parameter `user`
that contains a user info object

The user information object contains the following properties:

* `id` - The user's ID
* `name` - The username

The `getUserInfo` function can be used to check if a specific Last.fm
username exists.

## Getting a User's Top Artists

The list of a user's favorite artists can be loaded by calling the
`getTopArtists` function

```javascript
lastfm.getTopArtists(user, maxArtists, callback);
```

with the parameters:

* `user` - The Last.fm username
* `maxArtists` - The maximum number of artists to return
* `callback` - A callback function with a single parameter `artists`
that contains an array of artist objects. The array is sorted with the
most favorite artist at the lowest index.

Each artist object possesses the properties

* `mbid` - The artist's MusicBrainz identifier
* `name` - The artist's name

## Getting Upcoming Events of an Artist
