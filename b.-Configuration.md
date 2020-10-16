If you have not yet installed the bot, please go to the [installation guide](https://github.com/idinium96/tf2autobot/wiki/a.-Installation).

# Environment variables

The bot is configured through environment variables. These variables can be set using a file that the bot reads when it starts.

Create a new file inside the tf2autobot folder and call it `.env` and add the variables like in the [template.env](https://github.com/idinium96/tf2autobot/blob/master/template.env) file.

An alternative to environment files is the [PM2 ecosystem file](https://github.com/idinium96/tf2autobot/wiki/e.-Running-with-PM2), which is much more recommended to run your bot with (on a Linux based OS because running PM2 on Windows is somewhat buggy and can cause a lot of problems).

## Required

You are only required to add 4 variables, they are `STEAM_ACCOUNT_NAME`, `STEAM_PASSWORD`, `STEAM_IDENTITY_SECRET` and `STEAM_SHARED_SECRET`. You can get the identity secret and shared secret by authenticating the account with [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator).

Another 2 variables that are also needed are `ADMINS` and `KEEP`, which both will be your SteamID64.

## Backpack.tf API keys

The bot is made in a way so that you only need to give it an account and it will do the rest for you. If the environment variables `BPTF_ACCESS_TOKEN` or `BPTF_API_KEY` are missing, then the bot will sign in to backpack.tf by itself and get the API key and access token, which then you need to manually add the values to those respective variables.

<div align="center"><img src="https://cdn.discordapp.com/attachments/445226411461050380/697126889193603082/bptf-api-token.png" alt="listings" style="display: block; margin-left: auto; margin-right: auto;"></div>

From the above image, you need to copy the values (between the double quotes `""` of `apiKey` and `accessToken` keys) onto `BPTF_API_KEY` and `BPTF_ACCESS_TOKEN`, respectively.

The bot will also set the trade offer URL on backpack.tf, meaning that you don't need to sign in to backpack.tf at all to set up the bot.


## Other variables

You can find out the descriptions on all other variables (including all that has been mentioned above) [here](https://github.com/idinium96/tf2autobot#variables-in-ecosystemjson-summary).

***


Click [here](https://github.com/idinium96/tf2autobot/wiki/c.-Running-the-bot) to see how to run the bot.