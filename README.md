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
that contains a user object

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

## Getting Upcoming Events of an Artist

To get upcoming events of a specific artist, you may invoke the
`getEvents` functions

```javascript
lastfm.getEvents(artist, callback);
```

with the parameters:

* `artist` - The artist object for which events shall be loaded
* `callback` - A callback function with a single parameter `eventData`
which is an object with two properties - `artist` and `events`. The
`artist` field holds the initially specified `artist` object and can be
used to distinguish concurrent calls to the function. The `events`
property contains an array of event objects.

## Data Types

### User

A user object encapsulates a specific Last.fm user and exhibits the
following properties:

* `id` - The user's ID `[string]`
* `name` - The Last.fm username `[string]`

### Artist

An artist object describes a particular Last.fm artist and comprises of
the properties:

* `mbid` - The artist's MusicBrainz identifier
* `name` - The artist's name

### Venue

Venue objects identify locations at which events are hold. The contain
the fields:

* `id` - The venue's ID
* `name` - The venue's name
* `street` - The street address
* `zip` - The postal code
* `city` - The city in which the venue is located
* `country` - The country in which the venue is located
* `latitude` - The location's geographical latitude
* `longitude` - The location's geographical longitude

### Event

An event object represents a particular concert played by one or more
artists. It contains the following properties:

* `id` - The event's ID
* `name` - The event's name
* `startDate` - The starting date
* `endDate` - The ending date
* `canceled` - Whether the event has been canceled or not
* `headliner` - The lead artist
* `artists` - An array of all artists performing at the event
* `venue` - The event's location
