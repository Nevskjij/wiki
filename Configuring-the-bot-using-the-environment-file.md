Now that you have downloaded and installed the bot you can start with configuring your bot.

First, we will setup the environment file which you will use to configure the bot to your needs.

# Environment file and environment variables
## For the Windows setup
The bot is configured through environment variables. These variables can be set using a file that the bot reads when it starts.

Please ensure that you've file types extension viewer enabled on your PC settings (click [here](https://www.howtogeek.com/205086/beginner-how-to-make-windows-show-file-extensions/) if you are not sure what is this about). Use the [template.env](https://github.com/idinium96/tf2autobot/blob/master/template.env) file found on your tf2autobot folder and rename it to `.env` (yes, only a dot (`.`) and a word `env`). 

## For the Linux setup
The bot is configured through environment variables. These variables can be set using a file that the bot reads when it starts.

If you look at your `tf2autobot` folder you can already see a file called `template.ecosystem.json`

The first thing you should do is rename that file to `ecosystem.json`

# Required variables for the bot to start

To be able to start the bot, you need to set a few compulsory variables.

If you have followed the [Before you start](https://github.com/idinium96/tf2autobot/wiki/Before-you-start) guide you should already have your `STEAM_SHARED_SECRET` and `STEAM_IDENTITY_SECRET` ready.

## ✓ Your bot credentials

|        Variable         |   Type   | Description                                                                                                                                                                                                                                                                                                |
| :---------------------: | :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  `STEAM_ACCOUNT_NAME`   | `string` | The Steam account username of your bot account                                                                                                                                                      |
|    `STEAM_PASSWORD`     | `string` | The Steam account password of your bot account                                                                                                                                                                                                                                                                         |
|  `STEAM_SHARED_SECRET`  | `string` | You can find this in the `<yourBotSteamID>.maFile` file inside `~/SDA/maFiles` folder. Open the file using notepad and search for `"shared_secret": "agdgwegdgawfagxafagfkagusbuigiuefh=="` <-- take only this one (which is `agdgwegdgawfagxafagfkagusbuigiuefh==` in this example. Do not use this one, it is just an example). |
| `STEAM_IDENTITY_SECRET` | `string` | Same as above (but now search for `identity_secret`).                                                                                                                      |

**Q: Where can I get those secrets?**

-   A: You need to activate Steam Guard for your bot account using [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator)

## ✓ Backpack.tf token and API Key

If you have followed the [Before you start](https://github.com/idinium96/tf2autobot/wiki/Before-you-start) guide you should already have your `BPTF_ACCESS_TOKEN` and `BPTF_API_KEY` ready.

If you haven't, you can run your bot without this initially. On the first run, your bot will print out your bot backpack.tf access token and apiKey. You'll need to copy and paste these into your `ecosystem.json` or `.env` file ([see this image](https://cdn.discordapp.com/attachments/697415702637838366/697820077248086126/bptf-api-token.png)). If you want to find it manually:

|      Variable       |   Type   | Description                                                                                                                                             |
| :-----------------: | :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BPTF_ACCESS_TOKEN` | `string` | While logged into backpack.tf as your bot account go to https://backpack.tf/connections and click on `Show Token` under User Token.                                                                               |
|   `BPTF_API_KEY`    | `string` | While still logged into backpack.tf as your bot account go to https://backpack.tf/developer/apikey/view - fill in site URL (`http://localhost:4566/tasks`) and comments (`Check if a user is banned on backpack.tf`). |

## ✓ Owners' details and other compulsory variables

| Variable |    Type    |                                        Default                                         | Description                                                                                                                                                                                                                               |
| :------: | :--------: | :------------------------------------------------------------------------------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ADMINS` | `string[]` |                                         `[""]`                                         | Put your main SteamID64. Example - `["76561198013127982"]`. If you have multiple - `["76561198013127982", "76561198077208792"]`                                                                                                           |
|  `KEEP`  | `string[]` |                                         `[""]`                                         | Same as `ADMINS`, you must fill in **BOTH**.                                                                                                                                                                                              |
| `GROUPS` | `string[]` | → | Default groups are [tf2-automatic](https://steamcommunity.com/groups/tf2automatic) and [IdiNium's Trading Bot](https://steamcommunity.com/groups/IdiNiumNetwork) groups. If you have a Steam group, find your group ID and paste it here. |
| `ALERTS` | `string[]` |                                      `["trade"]`                                       | By default your bot will send a message/discord webhook every time a successful trade is made. Another option is `["none"]`.                                                                                                                |

Please ensure you fill in all of the above variables. In the templates, you can see the value for `ADMINS` and `KEEP` are `["<your steamid 64>"]` and `["<steamid of person to keep in friendslist>"]`, respectively.

Make sure to replace the whole `<your steamid 64>` and `<steamid of person to keep in friendslist>` with **YOUR STEAMID64**. You can find your SteamID64 by pasting your Steam Profile URL link to [SteamRep.com](https://steamrep.com/)

![How to get SteamID64](https://user-images.githubusercontent.com/47635037/96715154-be80b580-13d5-11eb-9bd5-39613f600f6d.gif)

# Full explanation of other environment variables

Table of contents
- [Prices.tf API token (outdated)](#pricestf-api-token) 
- [Metal crafting settings](#metal-crafting-settings)
- [Autokeys settings](#autokeys-feature)
- [Timezone settings](#your-time)
- [Escrow, Metal Overpay, Banned check](#set-to-true-if-want-to-allow)
- [Debug mode](#set-to-true-if-want-to-enable-debugging-notes-in-console)
- [Backpack.tf buy/sell order listing note](#backpacktf-sell-or-buy-order-listings-note-on-all-items-in-pricelist)
- [Discord server invite link](#discord-server-invite-link)
- [Discord Webhook configuration](#discord-webhook-configuration)
- [Manual Review Settings](#manual-review-settings)
- [Custom steam chat messages](#others)


## Prices.TF API token

|       Variable       |   Type   | Description                                              |
| :------------------: | :------: | -------------------------------------------------------- |
| `PRICESTF_API_TOKEN` | `string` | You can leave this empty. No need to fill it out at all. |

## Backpack.tf Autobump (re-list)

|      Variable       |   Type    | Default | Description                                                                                                                                                   |
| :-----------------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     `AUTOBUMP`      | `boolean` | `false` | **DEPRECATED** - Please consider donating to backpack.tf or buy backpack.tf Premium. If you enable this, your bot will re-list all listings every 30 minutes. |

## Metal crafting settings

| Variable | Type | Default | Description |
| :-----------------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `MINIMUM_SCRAP` | `integer` | `9` | If your bot has less, it will smelt reclaimed metal to maintain ample scrap metal supply. |
| `MINIMUM_RECLAIMED` | `integer` | `9` | If your bot has less, it will smelt refined metal to maintain ample reclaimed metal supply. |
| `METAL_THRESHOLD` | `integer` | `9` | If scrap/reclaimed metal has reached the minimum + threshold (max), it will combine the metal. |
| `DISABLE_CRAFTING_ METAL` | `boolean` | `false` | **NOT RECOMMENDED** to set is as `true` - it will cause your bot and the trade partner to not be able to trade because of missing scrap/reclaimed. |
| `DISABLE_CRAFTING_ WEAPONS` | `boolean` | `false` | Set to `true` **if you DO NOT** want your bot to automatically craft any duplicated/matched class craftable weapons. |
| `ENABLE_SHOW_ ONLY_METAL` | `boolean` | `true` | If set to `false`, it will show `[x keys, y ref]`, example: `(5 keys, 10 ref)`, instead of `[x ref]`, example: `(260 ref)`. |

### Autokeys feature
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
|               Variable                |   Type    | Default | Description                                                                                                                                                                |
| :-----------------------------------: | :-------: | :-----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|           `ENABLE_AUTOKEYS`           | `boolean` | `false` | If you set to `true`, your bot will automatically sell/buy keys based on the availability of the refined metals and keys in your bot inventory.                            |
|      `ENABLE_AUTOKEYS_BANKING`       | `boolean` | `false` | If set to `true`, your bot will bank keys (must also set `ENABLE_AUTOKEYS` to `true`). If current ref supply is in between min and max and keys > min, it will bank keys). |
|            `MINIMUM_KEYS`             | `number`  |   `3`   | When `current keys > minimum keys` (and if `current ref < minimum ref`), it will start selling keys, else, it will stop.                                                   |
|            `MAXIMUM_KEYS`             | `number`  |  `15`   | When `current keys < maximum keys` (and if `current ref > maximum ref`), it will start buying keys, else, it will stop.                                                    |
| `MINIMUM_REFINED_TO_ START_SELL_KEYS` | `number`  |  `30`   | Already explained in `MINIMUM_KEYS`.                                                                                                                                       |
| `MAXIMUM_REFINED_TO_ STOP_SELL_KEYS`  | `number`  |  `150`  | Already explained in `MAXIMUM_KEYS`.                                                                                                                                       |
|      `DISABLE_SCRAP_ADJUSTMENT`      | `boolean` | `true`  | Set to `false` to make an adjustment on the key price when selling or buying. It is not possible to do for key banking.                                                    |
|       `SCRAP_ADJUSTMENT_VALUE`       | `integer` |   `1`   | 1 scrap = 0.11 ref, 9 scrap = 1 ref                                                                                                                                        |
|    `AUTOKEYS_ACCEPT_UNDERSTOCKED`     | `boolean` | `false` | Set to `true` if you want your bot to accept trades that will lead to key become understocked.                                                                             |

\*\*This feature is meant to have your bot maintain enough pure in their inventory. Enabling "Autokeys - Banking" might cause this feature to not perform as intended.

### Set to true if want to disable

|                Variable                 |   Type    | Default | Description                                                                                                                                            |
| :-------------------------------------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
|        `DISABLE_INVENTORY_ SORT`        | `boolean` | `false` | Sort your bot's inventory.                                                                                                                             |
|           `DISABLE_LISTINGS`            | `boolean` | `false` | Temporarily disable trading while your bot is alive.                                                                                                   |
|           `DISABLE_MESSAGES`            | `boolean` | `false` | When `true`, people (that are friends with your bot) will be unable to send messages to you with "!message" command.                                      |
|    `DISABLE_SOMETHING_ WRONG_ALERT`     | `boolean` | `false` | Used to notify the owner if your bot has a queue problem/full inventory/is low in pure (if Autokeys is on).                                                |
|   `DISABLE_CRAFTWEAPON_ AS_CURRENCY`    | `boolean` | `false` | Set it as `true` if you don't want to set craft weapons as currency (0.05 ref).                                                                        |
| `DISABLE_GIVE_PRICE_ TO_INVALID_ITEMS`  | `boolean` | `false` | Set to `true` if you don't want `INVALID_ITEMS` (items that are not in your price list) to be priced using price from Prices.TF.                        |
|          `DISABLE_ADD_FRIENDS`          | `boolean` | `false` | Set to `true` if you don't want people to add your bot as a Steam friend (not recommended).                                                            |
|        `DISABLE_GROUPS_ INVITE`         | `boolean` | `false` | Set to `true` if you don't want your bot to invite people to join Steam groups **(You still need to have at least 1 group ID in the `GROUPS` array)**. |
| `DISABLE_CHECK_USES_ DUELING_MINI_GAME` | `boolean` | `false` | (must have 5 uses left). Set to `true` if you want your bot to buy Dueling Mini-Games regardless of how many uses are left.                            |
|    `DISABLE_CHECK_USES_ NOISE_MAKER`    | `boolean` | `false` | (must have 25 uses left). Set to `true` if you want your bot to buy Noise Makers regardless of how many uses are left.                                 |
|   `DISABLE_AUTO_REMOVE_ INTENT_SELL`    | `boolean` | `false` | By default, any pricelist entry with intent=sell will be automatically removed when the particular item is sold and no longer in the bot inventory.    |

### Set to true if want to enable

|           Variable            |   Type    | Default | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------------------: | :-------: | :-----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `NORMALIZE_ FESTIVIZED_ITEMS` | `boolean` | `false` | Set to `true` if you want your bot to recognize `Festivized` items as `Non-Festivized` items. For example, if your bot is selling a `Strange Australium Black Box`, but someone sent to your bot a Festivized version with the name `Festivized Strange Australium Black Box`, the bot by default will either decline or skip (depending on if you enable manual review) the offer because it's not a match. Thus, set to `true` if you want your bot to recognize `Festivized Strange Australium Black Box` as `Strange Australium Black Box`. |
| `NORMALIZE_ STRANGE_UNUSUAL`  | `boolean` | `false` | Set to `true` if you want Strange Unusuals (sku ends with `;strange`) to be recognized as normal Unusuals (sku doesn't end with `;strange`).                                                                                                                                                                                                                                                                                                                                                                                                    |

### Misc feature
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
|           Variable            |       Type       | Default | Description                                                                                                                                                                                                                                        |
| :---------------------------: | :--------------: | :-----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `TRADES_MADE_ STARTER_VALUE`  |    `integer`     |   `0`   | Used mainly for displaying how many total trades your bot has made found in your bot Steam Profile page (leave it 0 if you don't care about it, used for discord webhook).                                                                         |
|     `LAST_TOTAL_ TRADES`      |    `integer`     |   `0`   | Used if your polldata.json is getting bigger (which consumes a lot of RAM) but you want to keep the number of total successful trades that your bot has made (leave it 0 if you don't care about it).                                              |
| `TRADING_STARTING_ TIME_UNIX` | `integer` (Unix) |   `0`   | Also same as `LAST_TOTAL_TRADES`, but this is the latest time (leave it 0 if you don't care about it). To read more, check out my [Discord server post](https://discordapp.com/channels/664971400678998016/666909518604533760/707706994932449410). |

### Duped unusual check feature

|          Variable          |   Type    | Default | Description                                                                                                                 |
| :------------------------: | :-------: | :-----: | --------------------------------------------------------------------------------------------------------------------------- |
|    `ENABLE_DUPE_CHECK`     | `boolean` | `true`  | Enable/disable dupe check on unusuals.                                                                                      |
|      `DECLINE_DUPES`       | `boolean` | `false` | Explains itself.                                                                                                            |
| `MINIMUM_KEYS_ DUPE_CHECK` | `number`  |  `10`   | Explains itself.                                                                                                            |

### Set to true if want to skip

|            Variable             |   Type    | Default | Description                                                                                                                                                                                         |
| :-----------------------------: | :-------: | :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|   `SKIP_BPTF_ TRADEOFFERURL`    | `boolean` | `true`  | Not sure why this may not work. Please add a trade offer URL by yourself [here](https://backpack.tf/settings##general) (login as your bot Steam account).                                             |
|   `SKIP_ACCOUNT_ LIMITATIONS`   | `boolean` | `true`  | Used to check your account limitation. It's better to set to `true` if your bot's Steam account is already a [premium account](https://support.steampowered.com/kb_article.php?ref=3330-IAGK-7663). |
| `SKIP_UPDATE_ PROFILE_SETTINGS` | `boolean` | `true`  | This is just to set your bot's Steam profile to public so backpack.tf can load your bot inventory and etc correctly. If you already set everything to the public, just set this to `true`.              |

### Your time
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
Time will be used in the `!time` command and message sent to trade partners if their offer needs to be reviewed.

|         Variable         |   Type   | Default | Description                                                                                                                              |
| :----------------------: | :------: | :-----: | ---------------------------------------------------------------------------------------------------------------------------------------- |
|        `TIMEZONE`        | `string` |  `UTC`  | Please only use these [Timezone Format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). For example, `Asia/Kuala_Lumpur`. |
|  `CUSTOM_TIME_FORMAT`   | `string` |    →    | `MMMM Do YYYY, HH:mm:ss ZZ` - Please refer to [this article](https://www.tutorialspoint.com/momentjs/momentjs_format.htm)                |
| `TIME_ADDITIONAL_ NOTES` | `string` |  `""`   | Optional additional notes when the bot shows your current time - your active hours, etc.                                                 |

### Set to true if want to allow

|    Variable     |   Type    | Default | Description                                                                                                                              |
| :-------------: | :-------: | :-----: | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `ALLOW_ESCROW`  | `boolean` | `false` | Escrow = trade hold.                                                                                                                     |
| `ALLOW_OVERPAY` | `boolean` | `true`  | If people offer to overpay, your bot will accept. Set it to `false` if you want it to decline.                                              |
| `ALLOW_GIFT_ WITHOUT_NOTE` | `boolean` | `false` | Set this to `true` if you want your bot to accept any gift without the need for the trade partner to include anything in the offer message (Not recommended). |
| `ALLOW_BANNED`  | `boolean` | `false` | I think it's best to set as `false`. If set as `true`, your bot will trade with backpack.tf banned or steamrep.com scammer marked users. |

### Set time for the price to be updated in seconds

|    Variable     |   Type   |     Default     | Description                                                                                                                    |
| :-------------: | :------: | :-------------: | ------------------------------------------------------------------------------------------------------------------------------ |
| `MAX_PRICE_AGE` | `number` | `28800` (8 hrs) | If an item price hasn't been updated in longer than this amount of time, it will be triggered to check its price with Prices.tf. |

### Set to true if want to enable debugging notes in console

|   Variable   |   Type    | Default | Description                                                                                                                         |
| :----------: | :-------: | :-----: | ----------------------------------------------------------------------------------------------------------------------------------- |
|   `DEBUG`    | `boolean` | `true`  | Used to debug if any problem has occurred.                                                                                           |
| `DEBUG_FILE` | `boolean` | `true`  | Same as above, but this will create a file which can be sent to [issue](https://github.com/idinium96/tf2autobot/issues/new/choose). |

### Backpack.tf sell or buy order listings note on all items in pricelist
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
|      Variable       |   Type   |                                        Default                                         | Description              |
| :-----------------: | :------: | :------------------------------------------------------------------------------------: | ------------------------ |
| `BPTF_DETAILS_BUY`  | `string` | [see](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json#L85) | Your buy order message.  |
| `BPTF_DETAILS_SELL` | `string` | [see](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json#L86) | Your sell order message. |

**Parameters:**

-   `%name%` - display an item's name.
-   `%price%` - display items buying/selling price.
-   `%current_stock%` - display an items current stock (by default this is used in `BPTF_DETAILS_BUY`).
-   `%max_stock%` - display an item maximum stock (by default this is used in `BPTF_DETAILS_BUY`).
-   `%amount_trade%` - display the amount that can be traded (between the minimum and maximum stock, used in `BPTF_DETAILS_SELL`).
-   `%amount_can_buy%` - display the amount that the bot can buy (use it on `BPTF_DETAILS_BUY`).
-   `%keyPrice%` - display the current key rate (selling price). It will display as `Key rate: x ref/key` only if the item price includes x key. Otherwise, it will show as ✨.
-   `%dueling%` - display `(𝗢𝗡𝗟𝗬 𝗪𝗜𝗧𝗛 𝟱x 𝗨𝗦𝗘𝗦)` on only Dueling Mini-Game listings - prefer to only place this on `BPTF_DETAILS_BUY`. On other items it will show as ✨.

**Usage example:**

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/85929261-f3787200-b8e5-11ea-9ba8-b1acb12a5aad.PNG" alt="listings" style="display: block; margin-left: auto; margin-right: auto;"></div>

### Custom offer message

|    Variable     |   Type   | Default | Description                                                                                                                                         |
| :-------------: | :------: | :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `OFFER_MESSAGE` | `string` |  `""`   | Message that will appear when bot sends an offer to the trade partner. If left empty (""), it will print _**Powered by tf2-automatic**_ by default. |

## Discord server invite link
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
| Variable | Type | Default | Description |
| :-: | :-: | :-: | - |
| `DISCORD_SERVER_INVITE_LINK` | `string` | `""` | Must be your permenant Discord server invite link. You can leave it empty if you don't have one, it will be replaced with [tf2autobot Discord Server](https://discord.gg/ZrVT7mc) link.

## Discord Webhook Configuration
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
### Basic configuration on your embed preferences/appearances

`X = DISCORD_WEBHOOK`

|             Variable              |   Type   | Default | Description                                                                                                                                                                                |
| :-------------------------------: | :------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|        `DISCORD_OWNER_ID`         | `string` |  `""`   | Right click on yourself, click `Copy ID`, and paste it here. Make sure to enable developer mode on your Discord settings > Appearance > Advanced.                                          |
|           `X_USERNAME`            | `string` |  `""`   | Your Discord Webhook name. Example: ※Fumino⚡                                                                                                                                              |
|          `X_AVATAR_URL`           | `string` |  `""`   | Your Discord Webhook Avatar - must be in URL form. Example: https://gyazo.com/421792b5ea817c36054c7991fb18cdbc                                                                             |
| `X_EMBED_COLOR_IN_ DECIMAL_INDEX` | `string` |  `""`   | Embed color - you can find yours at [spycolor.com](https://www.spycolor.com/). Copy the one that says "has decimal index of: `take the value here`". Example: "9171753" for #8bf329 color. |

---

## Note on How to get `DISCORD_WEBHOOK_X_URL`

`X = SOMETHING_WRONG_ALERT | PRICE_UPDATE | TRADE_SUMMARY | OFFER_REVIEW | MESSAGE_FROM_PARTNER`

See this: https://gyazo.com/90e9b16d7c54f1b4a96f95b9fae93187 (settings in your respective channels)

---

### Queue alert

`X = DISCORD_WEBHOOK_SOMETHING_WRONG_ALERT`

|  Variable   |   Type    | Default | Description                                                                                                                                                               |
| :---------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `DISABLE_X` | `boolean` | `false` | Same as [`DISABLE_SOMETHING_WRONG_ALERT`](https://github.com/idinium96/tf2autobot#set-to-true-if-want-to-disable), but if set to `true`, it will send to your Steam Chat. |
|   `X_URL`   | `string`  |  `""`   | Discord Webhook URL for `SOMETHING_WRONG_ALERT`.                                                                                                                          |

### Pricelist update

`X = DISCORD_WEBHOOK_PRICE_UPDATE`

|             Variable             |   Type    | Default | Description                                                    |
| :------------------------------: | :-------: | :-----: | -------------------------------------------------------------- |
|           `DISABLE_X`            | `boolean` | `false` | Display price updates on the items that are in your pricelist. |
|             `X_URL`              | `string`  |  `""`   | Discord Webhook URL for `PRICE_UPDATE`.                        |
| `X_ADDITIONAL_DESCRIPTION_NOTE` | `string`  |  `""`   | You can add some notes there or just leave it empty.           |

### Successful trade summary

`X = DISCORD_WEBHOOK_TRADE_SUMMARY`

|             Variable              |    Type    | Default | Description                                                                                                                                                                                                                                                                                                                      |
| :-------------------------------: | :--------: | :-----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|            `DISABLE_X`            | `boolean`  | `false` | Display each successful trade summary on your trade summary/live-trades channel via Discord Webhook. If set to `true`, it will send to your Steam Chat.                                                                                                                                                                          |
|              `X_URL`              | `string[]` | `[""]`  | An array of the Discord Webhook URL for `TRADE_SUMMARY`. You will need to put it like this: `["yourDiscordWebhookLink"]`, or if you want to add more than one, you can do it like this: `["link1", "link2"]` (separate each link with a comma, make sure `link1` is your **own** Discord Webhook URL).                           |
|       `X_SHOW_QUICK_LINKS`        | `boolean`  | `true`  | Show the trade partner's quick links to their Steam profile, backpack.tf, and SteamREP pages.                                                                                                                                                                                                                                    |
|         `X_SHOW_KEY_RATE`         | `boolean`  | `true`  | Refer example below.                                                                                                                                                                                                                                                                                                             |
|        `X_SHOW_PURE_STOCK`        | `boolean`  | `true`  | Refer example below.                                                                                                                                                                                                                                                                                                             |
|        `X_SHOW_INVENTORY`         | `boolean`  | `true`  | Show the total amount of items in your bot's inventory.                                                                                                                                                                                                                                                                          |
| `X_ADDITIONAL_ DESCRIPTION_NOTE`  |  `string`  |  `""`   | If you want to do like in the example below, it will be `[YourText](Link)`                                                                                                                                                                                                                                                       |
|         `X_MENTION_OWNER`         | `boolean`  | `false` | Set this to `true` if you want to be mentioned on each successful trade.                                                                                                                                                                                                                                                           |
| `X_MENTION_OWNER_ ONLY_ITEMS_SKU` | `string[]` | `[""]`  | Support multiple items sku - let say you just want to be mentioned on every unusual and australium trade - just do`[";5;u", ";11;australium"]`. If you want to be mentioned on specific items, just fill in the full item sku like`["725;6;uncraftable"]`. To add more, just separate it with a comma between each sku `string`. |

**\*Note**: Want to feature your bots trades on the tf2autobot Discord server? Sure! I will give you the link upon request.

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/86468435-ffdb4f80-bd69-11ea-9ab6-a7f5be2c22f0.PNG" alt="trade-summary-full" style="display: block; margin-left: auto; margin-right: auto;"></div>

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/86468438-0073e600-bd6a-11ea-8bc0-040229c997d5.PNG" alt="trade-summary-full2" style="display: block; margin-left: auto; margin-right: auto;"></div>

### Offer review summary

`X = DISCORD_WEBHOOK_REVIEW_OFFER`

|              Variable              |   Type    | Default | Description                                                                                                                    |
| :--------------------------------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------ |
|            `DISABLE_X`             | `boolean` | `false` | Used to alert you on the trade that needs offer review via Discord Webhook. If set to `true`, it will send to your Steam Chat. |
|              `X_URL`               | `string`  |  `""`   | Discord Webhook URL for `REVIEW_OFFER`.                                                                                        |
| `X_DISABLE_MENTION_ INVALID_VALUE` | `boolean` | `false` | Set to `true` if you want your bot to not mention you on only `INVALID_VALUE` offers.                                            |
|        `X_SHOW_QUICK_LINKS`        | `boolean` | `true`  | Show the trade partner's quick links to their Steam profile, backpack.tf, and SteamREP pages.                                  |
|         `X_SHOW_KEY_RATE`          | `boolean` | `true`  | Refer example below.                                                                                                           |
|        `X_SHOW_PURE_STOCK`         | `boolean` | `true`  | Refer example below.                                                                                                           |

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/86468430-feaa2280-bd69-11ea-8f25-26a7a430b2e1.PNG" alt="only non-invalid-value2" style="display:block;margin-left:auto;margin-right:auto;"></div>

### Messages

`X = DISCORD_WEBHOOK_MESSAGE_FROM_PARTNER`

|       Variable        |   Type    | Default | Description                                                                                                                           |
| :-------------------: | :-------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------- |
|      `DISABLE_X`      | `boolean` | `false` | Used to alert you on any messages sent from the trade partner via Discord Webhook. If set to `true`, it will send to your Steam Chat. |
|        `X_URL`        | `string`  |  `""`   | Discord Webhook URL for `MESSAGE_FROM_PARTNER`.                                                                                       |
| `X_SHOW_ QUICK_LINKS` | `boolean` | `true`  | Show the trade partner's quick links to their Steam profile, backpack.tf, and SteamREP pages.                                         |

## Manual Review settings
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
|                Variable                 |    Type    | Default | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| :-------------------------------------: | :--------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|         `ENABLE_MANUAL_REVIEW`          | `boolean`  | `true`  | By default, offer with `INVALID_VALUE`/ `INVALID_ITEMS`/ `OVERSTOCKED`/ `UNDERSTOCKED`/ `DUPED_ITEMS`/ `DUPE_CHECK_FAILED` will be manually reviewed by you.                                                                                                                                                                                                                                                                                            |
|  `DISABLE_SHOW_REVIEW_ OFFER_SUMMARY`   | `boolean`  | `false` | Set to `true` if you do not want your bot to show the trade offer summary to the trade partner - it will only notify the trade partner that their offer is being held for review.                                                                                                                                                                                                                                                                           |
|      `DISABLE_REVIEW_ OFFER_NOTE`       | `boolean`  | `false` | By default, it will show notes on each [reason](https://github.com/idinium96/tf2autobot/wiki/FAQ#why-my-bot-dont-acceptdecline-the-trade-automatically)                                                                                                                                                                                                                                                                                                               |
|      `DISABLE_SHOW_ CURRENT_TIME`       | `boolean`  | `false` | By default, it will show the owner's time on offer review notification that the trade partner will receive.                                                                                                                                                                                                                                                                                                                                             |
| `DISABLE_ACCEPT_ INVALID_ITEMS_OVERPAY` | `boolean`  | `false` | Set this to `true` if you do not want your bot to accept trades with `INVALID_ITEMS` but the value of their side is greater than or equal to the value of your bot's side.                                                                                                                                                                                                                                                                              |
|  `DISABLE_ACCEPT_ OVERSTOCKED_OVERPAY`  | `boolean`  | `true`  | Set this to `false` if you want your bot to accept trades with `OVERSTOCKED` but the value of their side is greater than or equal to the value of your bot's side.                                                                                                                                                                                                                                                                                      |
| `DISABLE_ACCEPT_ UNDERSTOCKED_OVERPAY`  | `boolean`  | `true`  | Set to `false` if you want your bot to accept a trade with `UNDERSTOCKED` but with their value more or equal to our value.                                                                                                                                                                                                                                                                                                                              |
|   `DISABLE_AUTO_ DECLINE_OVERSTOCKED`   | `boolean`  | `true`  | Set this to `false` if you want your bot to decline an offer with **ONLY** `OVERSTOCKED` reason (manual review must be enabled.).                                                                                                                                                                                                                                                                                                                       |
|  `DISABLE_AUTO_ DECLINE_UNDERSTOCKED`   | `boolean`  | `true`  | Set this to `false` if you want your bot to decline an offer with **ONLY** `UNDERSTOCKED` reason (manual review must be enabled.)                                                                                                                                                                                                                                                                                                                       |
|  `DISABLE_AUTO_ DECLINE_INVALID_VALUE`  | `boolean`  | `false` | Set this to `true` if you do not want your bot to automatically decline trades with **ONLY** `INVALID_VALUE` (which did not match the exception sku(s) and exception value).                                                                                                                                                                                                                                                                            |
|   `AUTO_DECLINE_ INVALID_VALUE_NOTE`    |  `string`  |  `""`   | Your custom note on why the trade got declined. The default is nothing.                                                                                                                                                                                                                                                                                                                                                                                     |
|     `INVALID_VALUE_ EXCEPTION_SKUS`     | `string[]` | `[""]`  | An array of sku that will skip `INVALID_VALUE` if the difference between the bot's value and their value is not more than exceptional value. Let's say your bot is selling an Unusual and someone sent an offer with 0.11 ref less - you want your bot to accept it anyway! By default, it will check only for Unusuals and Australiums: `[";5;u", ";11;australium"]`. You can also leave it empty (`[""]`) so all with `INVALID_VALUE` will be notified. |
| `INVALID_VALUE_ EXCEPTION_VALUE_IN_REF` |  `number`  |   `0`   | - Exception value for the sku(s) that you set above. The default is `0` (no exception).                                                                                                                                                                                                                                                                                                                                                                     |
|          `INVALID_VALUE_NOTE`           |  `string`  |  `""`   | Your custom `INVALID_VALUE` note.                                                                                                                                                                                                                                                                                                                                                                                                                       |
|         \*`INVALID_ITEMS_NOTE`          |  `string`  |  `""`   | Your custom `INVALID_ITEMS` note.                                                                                                                                                                                                                                                                                                                                                                                                                       |
|          \*`OVERSTOCKED_NOTE`           |  `string`  |  `""`   | Your custom `OVERSTOCKED` note.                                                                                                                                                                                                                                                                                                                                                                                                                         |
|          \*`UNDERSTOCKED_NOTE`          |  `string`  |  `""`   | Your custom `UNDERSTOCKED` note.                                                                                                                                                                                                                                                                                                                                                                                                                        |
|           \*`DUPE_ITEMS_NOTE`           |  `string`  |  `""`   | Your custom `DUPE_ITEMS` note.                                                                                                                                                                                                                                                                                                                                                                                                                          |
|       \*`DUPE_CHECK_FAILED_NOTE`        |  `string`  |  `""`   | Your custom `DUPE_CHECK_FAILED` note.                                                                                                                                                                                                                                                                                                                                                                                                                   |
|            `ADDITIONAL_NOTE`            |  `string`  |  `""`   | Your custom `ADDITIONAL` note.                                                                                                                                                                                                                                                                                                                                                                                                                          |

---

**Notes:**
On each reason **except** `INVALID_VALUE`, you can put `%name%` to list all the items that are on that reason, and `%isName%` for the plural of "is" - where if `%name%` is just 1 item, it will use "is", else if more then one item, it will use "are".

Example:
Let say the trade contains items with `INVALID_ITEMS`. The items are Dueling Mini-Game, Secret Saxton.

-   You use custom `INVALID_ITEMS` note as: `"%name% %isName% not in my pricelist. Please wait for my owner to check it."`

-   What the trade partner will receive: `"Dueling Mini-Game, Secret Saxton is not in my pricelist. Please wait for my owner to check it."`

For `OVERSTOCKED` and `UNDERSTOCKED`, parameter `%name%` will print out a list of `amountCanTrade - item_name` (example, `1 - Secret Saxton, 0 - Jag`).

**Default Notes:**

-   `INVALID_VALUE`: `You're taking too much in value.`
-   `INVALID_ITEMS`: `%name% is|are not in my pricelist.`
-   `OVERSTOCKED`: `I can only buy %name% right now.`
-   `UNDERSTOCKED`: `I can only sell %amountCanTrade% - %name% right now.`
-   `DUPED_ITEMS`: `%name% is|are appeared to be duped.`
-   `DUPE_CHECK_FAILED`: `I failed to check for duped on %name%.`

---

## Others
[Go back to Table of contents](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#full-explanation-of-other-environment-variables)
|              Variable               |   Type   | Default | Description                                                                                                                                                                                                                                                                                 |
| :---------------------------------: | :------: | :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|       `ENABLE_ONLY_ PLAY_TF2`       | `boolean`| `false` | Set to `true` if you want your bot to only play Team Fortress 2, which will ignore the below variable.                                                                                                                                                |
|     `CUSTOM_PLAYING_ GAME_NAME`     | `string` |  `""`   | Custom name of the game your bot is playing. Limited to only 45 characters. Example: https://gyazo.com/308e4e05bf4c49929520df4e0064864c (you do not need to include `- tf2-automatic`, just your custom game name.)                                                                         |
|      `CUSTOM_WELCOME_ MESSAGE`      | `string` |  `""`   | Your custom `WELCOME_MESSAGE` note. Two parameters: `%name%` (display trade partner's name) and `%admin%` (if admin, it will use "!help", else "!how2trade").                                                                                                                               |
| `CUSTOM_I_DONT_KNOW_ WHAT_YOU_MEAN` | `string` |  `""`   | Your custom note when people send the wrong command.                                                                                                                                                                                                                                        |
|     `CUSTOM_HOW2TRADE_ MESSAGE`     | `string` |  `""`   | Your custom `HOW2TRADE` note.                                                                                                                                                                                                                                                               |
|      `CUSTOM_SUCCESS_ MESSAGE`      | `string` |  `""`   | Your custom `SUCCESS` note.                                                                                                                                                                                                                                                                 |
|     `CUSTOM_DECLINED_ MESSAGE`      | `string` |  `""`   | Your custom `DECLINED` note. Two parameters can be used - `%reason%` and `%invalid_value_summary%`. |
|    `CUSTOM_TRADED_ AWAY_MESSAGE`    | `string` |  `""`   | Your custom note when the bot fails to trade because the item is traded away.                                                                                                                                                                                                               |
| `CUSTOM_CLEARING_ FRIENDS_MESSAGE`  | `string` |  `""`   | Your custom note when the bot is removing friends to add someone else Usable parameter - `%name%` (display trade partner's name).