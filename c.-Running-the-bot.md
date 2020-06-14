# Run through command prompt/terminal

Once you have downloaded the bot, installed the dependencies, and created the config, you can then run the bot. You do this by navigating to the tf2autobot folder using the command prompt or terminal and type `node dist/app.js` into it.

# Errors on startup

## Missing dependencies

You are missing the dependencies, see the [installation guide](https://github.com/idinium96/tf2autobot/wiki/a.-Installation#installing-modules).

## Missing required environment variable

You are missing one or more of `STEAM_ACCOUNT_NAME`, `STEAM_PASSWORD`, `STEAM_SHARED_SECRET`, or `STEAM_IDENTITY_SECRET`. Add them to the environment variables and start the bot again.

## HTTP error xxx

This is a temporary error, it depends on the error code what you should do, but you can retry running the bot on most of them.

## Other errors

Please visit: https://github.com/idinium96/tf2autobot/wiki/Errors

Or check the [GitHub issues](https://github.com/idinium96/tf2autobot/issues) to see if someone has gotten the error before, if not, then please create an issue with the error.


***


Click [here](https://github.com/idinium96/tf2autobot/wiki/d.-Setup-on-VPS) to see how to set up the bot on a VPS to run it 24/7.