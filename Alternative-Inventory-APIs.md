TF2Autobot relies heavily on the Steam API for loading different users' inventories so that it can send trades and provide other core functionality. In recent months the Steam API endpoint for loading inventories has added highly restrictive rate limiting, making it more difficult for trading bots of all types to function properly.

Alternative inventory APIs are services that use various methods to more reliably get the inventory data that TF2Autobot needs. These are paid services that can improve your bot's response time and reliability if you are experiencing issues with loading inventories.

# Setup Guide

There currently are two alternative inventory API options. SteamSupply can be paid for with TF2 keys and generally has cheaper rates, and has the option to pay per request as well as paying for a certain number of requests per day. SteamAPIs can be paid for with PayPal (balance, credit or debit card) or Bitcoin, and there is no option to pay per request; payment is for a certain number of requests per day.

Note that if using an alternative inventory API, **you must choose only one option**. While you can switch between them (or back to Steam's official API) later on, only (at most) one at a time may be actively used.

## SteamSupply

To start using the SteamSupply inventory API, navigate to https://steam.supply/ and click the "Login" button in the top right. This will redirect you to Steam to authenticate you.

Once logged in, click on your username and avatar in the top right, then click "My Settings" in the dropdown menu.

This page will show you your API key and allows you to choose from different options for pay type. You can pay per request, or pay per month for a certain number of requests per day, up to the most expensive 40,000 requests per day. Choose the option under "Pay Type" that makes the most sense for you (you can always change this later). Under "Add Funds", choose the "Steam Keys" option. Select the text starting with `API:` in the white box and copy it, then click the "Trade Url" button to go to a new Steam trade offer with the rate checking bot. **Before doing anything else, make sure you paste the exact text from the white box into the trade message, and do not make any changes to it after doing so.** Add however many TF2 keys you want to your side of the trade, then click to confirm and make the offer as usual, and verify with Steam Guard as needed. The offer should go through quickly.

Now, go back to the SteamSupply settings page (https://steam.supply/settings) to verify that you have some credits. You can now copy your API key and paste it into your `.env` file with a line of this format:
`STEAMSUPPLY_API_KEY=<paste your api key here>`

Send the message `!config inventoryApis.steamSupply.enable=true` to your bot through Steam or Discord, then restart it. Your bot will now use the SteamSupply API when it needs to load inventories.

You can go back to the SteamSupply settings page to check how many requests your bot has made, how much credit you have left, and set up notifications to alert you when your credits are running low. Follow the same process as before to add additional funds as needed.

## SteamAPIs

To start using the SteamAPIs inventory API, navigate to https://steamapis.com/ and click the "Sign in through Steam" button in the top right. This will redirect you to Steam to authenticate you.

Once logged in, click your username and avatar in the top right, and click the "Upgrade" option to see a summary of each API endpoint and its price per hour or month. The one we are concerned with is the "Steam > Inventory" API endpoint. Use the hourly and monthly price to determine how much balance you wish to start with. (Note that there are also different options for how often you may use this API; to view pricing for these options, click the "Enable Endpoints" dropdown and select "Steam Inventory". Once that is done, scroll down and click the dropdown under "Inventory Limits" to view the options and pricing for how often the inventory endpoint can be used. Most bot owners should be fine with the minimum limits with no additional payment. Don't click "Save changes" at this point.)

Once you have an idea of how much balance you wish to begin with, click on your name and avatar again, and this time click "Add Funds" in the dropdown. Payment is denominated in euro, and the minimum balance top-up is €5. Choose how many euro you wish to add, then click either the blue PayPal button or the green Bitcoin button to pay with the corresponding method, and follow the instructions.

Once you have some balance, navigate back to https://steamapis.com/, sign in again if needed, click on your username and avatar, and select "Upgrade" from the dropdown. Click the "Enable Endpoints" field and select "Steam Inventory". (At this point, if you need higher limits, you can select those as well by scrolling down to the "Default" field under "Inventory Limits" and clicking it.) Click "Save changes" when you are done.

Once this is done, click your avatar and username on the top right, select "API Access" from the drop down, and under "Generate a New Key" click the "Yes, please!" button (do this first to avoid issues with the API not recognizing access). Finally, copy your API key and paste it into your `.env` file with a line of this format:
`STEAMAPIS_API_KEY=<paste your api key here>`

Send the message `!config inventoryApis.steamApis.enable=true` to your bot through Steam or Discord, then restart it. Your bot will now use the SteamAPIs inventory API when it needs to load inventories.

You can go back to the SteamAPIs API Access page to check how many requests your bot has made and how much balance you have remaining. You can also go back to the Add Funds page to top up your balance in the same way as before.

# Additional Notes

While setting up an alternative inventory API for the first time requires the bot to be restarted, disabling or enabling an already set up API does not, as long as you are not changing the API key. Simply send `!config inventoryApis.{name}.enable=true` to your bot through Steam or Discord to enable an alternative inventory API (replacing `{name}` with `steamSupply` or `steamApis` as applicable), or send the same command with `false` at the end instead of `true` to disable it. If all alternative inventory APIs are disabled (which is the default), the bot will directly use Steam's inventory API.