# Hub

The hub is active on `http://hub.gig.tech`


## Installation

All the code for the Hub can be found on https://github.com/g8os/hub

The README explains how to deploy your own instance.

Some important remarks:

- Create an ItsYou.online API key in order to get a client secret
- Make sure to set the callback URL, including `_iyo_callback`
- Compile Caddy with the OAuth plugin for ItsYou.online, available from https://github.com/itsyouonline/caddy-integration
- Install JumpScale from the correct branch: `8.2.0`, this version contains all dependencies needed by flist, used on the Hub, including the G8 storage client (`g8storclient`)
- Deploy an ARDB instance for the storage
  - Make it read-write (default)
  - No specific backend is required, RocksDB is a good choice
  - Expose this ARDB instance  as `PRIVATE_ARDB_` in the config
  - Don't expose it publicly
- Deploy a Redis instance
  - In slave-of mode
  - Make it read-only (default)
  - Expose this Redis instance as `PUBLIC_ARDB_` in the config
  - Exposed it publicly


## Testing

To make sure everything works:

- You should be able to access the Hub front page, click on the `Upload my files` button, and able to login with ItsYou.online
- On the upload page, you should see your username in the top right corner
- Create a small `.tar.gz` file with anything you want on it, and upload it
- The summary page should appear with all links working properly