## Changelog ##
* v1.4.0 (2016-06-26)
    * Ported to Python 3
    * PEP8 styling applied across codebase
    * Added Docker packaging support
    * Removed unowallet_iofeeds and socketio stuff
    * Move armory-utxsvr into its own repo
    * Fixes for timezone in generated/parsed datetimes
    * Update "reparse" command logic to make it like unoparty-lib
    * Pegged deps to specific versions
    * Added ability to disable file logging for main log and tx log
* v1.3.1 (2016-01-24)
    * Modify blockfeed logic to work with reorgs properly again with the undolog fix introduced in `unoparty-lib` 9.53.0.
    * Enhance blockfeed error recovery logic to make more robust and minimize/remove chance of blockfeed hangs.
    * `/_api` handler includes extra fields: `unoparty-server_caught_up` and improved reporting of error conditions.
    * Code upgraded to work with pymongo >= 3.1
* v1.3.0 (2015-10-31)
    * Fixes periodic `blockfeed` hanging issue (where `unoblock` would still run, but not process new blocks from `unoparty-server`)
    * Block processing is much more robust now if an exception is encountered (e.g. unoparty-server goes down). Should prevent additional hanging-type issues
    * Tweaked `blockfeed` "caught up" checking logic. Should be more reliable
    * Simplified `blockchain` module -- we call API methods on `unoparty-server` now, whereever possible, instead of reimplementing them on `unoblock`
    * Enhance the information returned with `GET /_api`. Several new parameters added, including `ERROR` for easier diagnosing of most common error conditions.
    * `GET /_api` now returns CORS headers, allowing it to be used with cross domain requests
    * Added this `ChangeLog.md` file
* v1.2.0 (2015-09-15)
    * Move most unoblock functionality into plug-in modules.
    * Pegs the pymongo library version, to avoid incompatibility issues with pymongo 3.0
    * Improves exception logging for exceptions that happen within a greenlet thread context
    * Fixes an issue with an exception on reorg processing (from unoparty-server's message feed).
    * Modifies the state flow with rollbacks to streamline and simplify things a bit
* 1.1.1 (2015-03-23)
    * Fix some (uncaught) runtime errors that can cause significant stability problems in Unoblock in certain cases.
    * Properly implements logging of uncaught errors to the unoblock log files.
* 1.1.0 (2015-02-06)
    * Updated to work with the new architecture of unoparty 9.49.4 (the configuration options have been adjusted to be like unoparty, e.g. no more --data-dir)
    * new configuration file locations by default
    * Added setup.py for setuptools / pip
* 1.0.1 (2015-01-23)
    * block state variable naming change
    * get_jsonrpc_api() fix with abort_on_error=False
    * bug fix with URL fetching, abort_on_error setting
    * Fix for ambivalent variable name
    * fix division per zero
* 1.0.0 (2015-01-05)
    * MAJOR: Added plugin (modular) functionality. unoblockd can now be easily extended to support custom functionality
    * Increased JSON API request timeout to 120 seconds
    * Implemented support for new order_match id format
    * Implemented always trying/retrying for RPC calls
    * Removed Callback and RPS
    * Modularized Unoblockd functionality & plugin interface for third-party modules
    * Optimized blockfeeds.py
    * Fixed the difference of one satoshi between BTC balances returned by unopartyd and unoblockd
    * Implemented an alternative for unopartyd api get_asset_info() method to speed up the login in unowallet for wallet with a lot of assets
    * Updated versions of deps (fixes issue with fetching SSL urls)
    * Fixed the issue with passing JSON data in POST requests
    * Added rollback command line argument and RollbackProcessor
