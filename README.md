[![Slack Status](http://slack.unoparty.io/badge.svg)](http://slack.unoparty.io)

unoblock
==============

`unoblock` provides additional services to Unowallet beyond those offered in the API provided by `unoparty-server`. It features a full-fledged JSON RPC-based API, which services Unowallet as well as any 3rd party services which wish to use it. `unoblock` has an extensible architecture, and developers may write custom plugins for it, which are loaded dynamically and allow them to extend `unoblock` with new parsing functionality, write gateways to other currencies or services, and much more.

With its set of core-plugins, `unoblock` provides a more high-level data processing, and an API that layers on top of `unoparty-server`’s API. `unoblock` generates and allows querying of data such as market and price information, trade operations, asset history, and more. It is used extensively by Unowallet itself, and is appropriate for use by applications that require additional API-based functionality beyond the scope of what `unoparty-server` itself provides.

# Installation

For a simple Docker-based install of the Counterparty software stack, see [this guide](http://unoparty.io/docs/federated_node/).

# Manual installation

(Linux only.) First, install `mongodb` and `redis`, and have an instance of `unotaniumd` (`addrindex` branch) and [`unoparty-server`](https://github.com/terhnt/unoparty-lib) running.

Then, download and install `unoblock`:

```
$ git clone https://github.com/terhnt/unoblock.git
$ cd unoblock
$ sudo pip3 install -r requirements.txt
$ sudo python3 setup.py install
```

Then, launch the daemon via the following command, with the passwords set as appropriate:

```
$ unoblock --backend-password=rpc --unoparty-password=rpc server
```

Further command line options are available via:

* `$ unoblock --help`

# License notices

This product will download/use GeoLite2 data created by MaxMind, available from
<a href="https://dev.maxmind.com/geoip/geoip2/geolite2/">https://dev.maxmind.com/geoip/geoip2/geolite2/</a>. Under **Creative Commons Corporation Attribution-ShareAlike 4.0 International License** (the “Creative Commons License”)
