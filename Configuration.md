If you have not yet installed the bot, please go to the [installation guide](https://github.com/Nicklason/tf2-automatic/wiki/Installation).

# Environment variables

The bot is configured through environment variables. These variables can be set using a file that the bot reads when it starts.

Create a new file inside the tf2-automatic folder and call it `.env` and add the variables like in the [template.env](https://github.com/Nicklason/tf2-automatic/blob/master/template.env) file.

An alternative to environment files is the [PM2 ecosystem file](https://github.com/Nicklason/tf2-automatic/wiki/PM2).

## Required

You are only required to add 4 variables, they are `STEAM_ACCOUNT_NAME`, `STEAM_PASSWORD`, `STEAM_IDENTITY_SECRET` and `STEAM_SHARED_SECRET`. You can get the identity secret and shared secret by authenticating the account with [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator).

## Backpack.tf API keys

The bot is made in a way so that you only need to give it an account and it will do the rest for you. If the environment variables `BPTF_ACCESS_TOKEN` or `BPTF_API_KEY` are missing, then the bot will sign in to backpack.tf by itself and get the API key and access token. The bot will also set the trade offer URL on backpack.tf, meaning that you don't need to sign in to backpack.tf at all to set up the bot.


***


Click [here](https://github.com/Nicklason/tf2-automatic/wiki/Running-the-bot) to see how to run the bot.