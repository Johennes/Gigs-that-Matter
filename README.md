jquery.lastfm
=============

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A jQuery plugin for convenient access to the Last.fm API

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
lastfm.getEvents(mbid, callback);
```

with the parameters:

* `mbid` - The MusicBrainz identifier of the artist for which events
shall be loaded
* `callback` - A callback function with two parameters, `mbid` and
`events`. The `mbid` parameter holds the initially specified MusicBrainz
identifier and can be used to distinguish concurrent calls to the
function. The `events` parameter contains an array of event objects.

## Data Types

### User

A user object encapsulates a specific Last.fm user and exhibits the
following properties:

* `id` `[string]` - The user's ID
* `name` `[string]` - The Last.fm username

### Artist

An artist object describes a particular Last.fm artist and comprises of
the properties:

* `mbid` `[string]` - The artist's MusicBrainz identifier
* `name` `[string]` - The artist's name

### Venue

Venue objects identify locations at which events are hold. The contain
the fields:

* `id` `[string]` - The venue's ID
* `name` `[string]` - The venue's name
* `street` `[string]` - The street address
* `zip` `[string]` - The postal code
* `city` `[string]` - The city in which the venue is located
* `country` `[string]` - The country in which the venue is located
* `latitude` `[float]` - The location's geographical latitude
* `longitude` `[float]` - The location's geographical longitude

### Event

An event object represents a particular concert played by one or more
artists. It contains the following properties:

* `id` `[string]` - The event's ID
* `name` `[string]` - The event's name
* `startDate` `[Date]` - The starting date
* `endDate` `[Date]` - The ending date
* `canceled` `[boolean]`  - Whether the event has been canceled or not
* `headliner` `[string]` - The lead artist. Note that this is not an
artist object but merely the headliner's name as string.
* `artists` `[Array]` - An array of all artists performing at the event.
Note that the array contains only the artists' names but not full artist
objects.
* `venue` `[Venue]`  - The event's location
