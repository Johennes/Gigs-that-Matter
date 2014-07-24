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
`getUserInfo` function.

```javascript
lastfm.getUserInfo('some-username', function(user) {
  // ...
});
```

The user information object is passed back to you in a callback function
and contains the following properties:

* `id` - The user's ID
* `name` - the username

The `getUserInfo` function can be used to check if a specific Last.fm
username exists.

## Getting a User's Top Artists

## Getting Upcoming Events of an Artist
