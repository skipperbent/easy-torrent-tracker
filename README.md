# Easy Torrent Tracker

Easy, simple and yet fast torrent tracker created in PHP.

Based on Nsuan's incredible work, source:
https://gist.github.com/nsuan/1967006

## Pre-note

Owners of trackers are putting on an extremely hard task in maintaining their trackers and dealing with their trackers being taken down or hosts forcing them to shut down, 
even though the service is perfectly legal. And most of the people administering trackers don't make any money, as there's no way to advertise using a tracker. 
That's why we need to show them support and help them out by creating as many small trackers as possible.

As you can see in the source file, trackers doesn't store any information about the content that is being shared - it only connects peers to each other.

## Installation

- Copy `announce.php` to your web-server
- Create a new text-file that will act as a database for enabled peers.
- Change the `__LOCATION_PEERS` option with the location of your database file.
- Change the `__REDIR_BROWSER` option to redirect to a url describing your tracker.

**Tip:** You can enable debugging by changing `DEBUG_ENABLE` option and adding the `?debug` param to your tracker.

## Options

### `__DEBUGGING_ENABLED` `bool`

Enable or disable debugging.
This allows anyone to see the entire peer database by appending ?debug to the announce URL

### `__INTERVAL` `int`

How often should clients pull server for new clients? (Seconds)

### `__INTERVAL_MIN` `int`

What's the minimum interval a client may pull the server? (Seconds)
Some bittorrent clients does not obey this

### `__CLIENT_TIMEOUT` `int`

How long should we wait for a client to re-announce after the last announce expires? (Seconds)

### `__NO_PEER_ID` `bool`

Skip sending the peer id if client does not want it?
Hint: Should be set to true

### `__NO_SEED_P2P` `bool`

Should seeders not see each others?
Hint: Should be set to true

### `__LOCATION_PEERS` `string`

Where should we save the peer database
On Linux, you should use `/dev/shm` as it is very fast.
On Windows, you will need to change this value to some other valid path such as `C:/Peers.txt`

### `__ENABLE_SHORT_ANNOUNCE` `bool`

Should we enable short announces?
This allows NATed clients to get updates much faster, but it also takes more load on the server. (This is just an experimental feature which may be turned off)

### `__REDIR_BROWSER` `string`

In case someone tries to access the tracker using a browser, redirect to this URL or file
