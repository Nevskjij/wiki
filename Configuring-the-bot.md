Now that you have downloaded and installed the bot you can start configuring your bot.

First, we will set up the environment file, which you will use to configure the bot to your needs.

# Environment File and Environment Variables

## - Linux
<details>
<summary>CLICK HERE IF YOU ARE RUNNING THE BOT ON LINUX</summary>

For Linux, the bot is configured through environment variables that can be set using a file called `ecosystem.json` that the bot reads when it starts.

The content of `ecosystem.json` file:

```
{
    "apps": [
        {
            "name": "tf2autobot",
            "script": "dist/app.js",
            "exec_mode": "fork",
            "shutdown_with_message": false,
            "max_memory_restart": "1500M",
            "kill_retry_time": 30000,
            "kill_timeout": 60000,
            "out_file": "NULL",
            "error_file": "NULL",
            "env": {
                "NODE_ENV": "production",

                "STEAM_ACCOUNT_NAME": "",
                "STEAM_PASSWORD": "",
                "STEAM_SHARED_SECRET": "",
                "STEAM_IDENTITY_SECRET": "",

                "BPTF_ACCESS_TOKEN": "",
                "BPTF_API_KEY": "",

                "ADMINS": ["<your steamid 64>"],
                "KEEP": ["<steamid of person to keep in friendslist>"],
                "ITEM_STATS_WHITELIST": [],
                "GROUPS": ["103582791469033930"],
                "ALERTS": ["trade", "version"],

                "ENABLE_SOCKET": true,
                "CUSTOM_PRICER_URL": "",
                "CUSTOM_PRICER_API_TOKEN": "",

                "SKIP_BPTF_TRADEOFFERURL": true,
                "SKIP_UPDATE_PROFILE_SETTINGS": true,

                "TIMEZONE": "",
                "CUSTOM_TIME_FORMAT": "",
                "TIME_ADDITIONAL_NOTES": "",

                "DEBUG": true,
                "DEBUG_FILE": true,

                "ENABLE_HTTP_API": false,
                "HTTP_API_PORT": 3001
            }
        }
    ]
}
```

Modify the [template.ecosystem.json](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json) file found in your `tf2autobot/` folder, renaming it to `ecosystem.json`. This file will be the file you edit when you want to configure your bot, using the below variables.

<details>
<summary>ECOSYSTEM.JSON FOR TWO BOTS</summary>

```
{
    "apps": [
        {
            "name": "tf2autobot",
            "script": "dist/app.js",
            "exec_mode": "fork",
            "shutdown_with_message": false,
            "max_memory_restart": "1500M",
            "kill_retry_time": 30000,
            "kill_timeout": 60000,
            "out_file": "NULL",
            "error_file": "NULL",
            "env": {
                "NODE_ENV": "production",

                "STEAM_ACCOUNT_NAME": "",
                "STEAM_PASSWORD": "",
                "STEAM_SHARED_SECRET": "",
                "STEAM_IDENTITY_SECRET": "",

                "BPTF_ACCESS_TOKEN": "",
                "BPTF_API_KEY": "",

                "ADMINS": ["<your steamid 64>"],
                "KEEP": ["<steamid of person to keep in friendslist>"],
                "ITEM_STATS_WHITELIST": [],
                "GROUPS": ["103582791469033930"],
                "ALERTS": ["trade", "version"],

                "ENABLE_SOCKET": true,
                "CUSTOM_PRICER_URL": "",
                "CUSTOM_PRICER_API_TOKEN": "",

                "SKIP_BPTF_TRADEOFFERURL": true,
                "SKIP_UPDATE_PROFILE_SETTINGS": true,

                "TIMEZONE": "",
                "CUSTOM_TIME_FORMAT": "",
                "TIME_ADDITIONAL_NOTES": "",

                "DEBUG": true,
                "DEBUG_FILE": true,

                "ENABLE_HTTP_API": false,
                "HTTP_API_PORT": 3001
            }
        },
        {
            "name": "tf2autobot",
            "script": "dist/app.js",
            "exec_mode": "fork",
            "shutdown_with_message": false,
            "max_memory_restart": "1500M",
            "kill_retry_time": 30000,
            "kill_timeout": 60000,
            "out_file": "NULL",
            "error_file": "NULL",
            "env": {
                "NODE_ENV": "production",

                "STEAM_ACCOUNT_NAME": "",
                "STEAM_PASSWORD": "",
                "STEAM_SHARED_SECRET": "",
                "STEAM_IDENTITY_SECRET": "",

                "BPTF_ACCESS_TOKEN": "",
                "BPTF_API_KEY": "",

                "ADMINS": ["<your steamid 64>"],
                "KEEP": ["<steamid of person to keep in friendslist>"],
                "ITEM_STATS_WHITELIST": [],
                "GROUPS": ["103582791469033930"],
                "ALERTS": ["trade", "version"],

                "ENABLE_SOCKET": true,
                "CUSTOM_PRICER_URL": "",
                "CUSTOM_PRICER_API_TOKEN": "",

                "SKIP_BPTF_TRADEOFFERURL": true,
                "SKIP_UPDATE_PROFILE_SETTINGS": true,

                "TIMEZONE": "",
                "CUSTOM_TIME_FORMAT": "",
                "TIME_ADDITIONAL_NOTES": "",

                "DEBUG": true,
                "DEBUG_FILE": true,

                "ENABLE_HTTP_API": false,
                "HTTP_API_PORT": 3001
            }
        }
    ]
}
```

</details>

<details>
<summary>ECOSYSTEM.JSON FOR MORE THAN TWO BOTS</summary>

You should feel familiar with the layout of the ecosystem.json from the example of the ecosystem.json for two bots.

Every bot is an object inside your `apps` array. The bot's environment starts with a curly bracket and ends with one.
</details>

</details>

## - Windows
<details>
<summary>CLICK HERE IF YOU ARE RUNNING THE BOT ON WINDOWS</summary>

For Windows, the bot is configured through environment variables that can be set using a file (`.env`) that the bot reads when it starts.

The content of the `.env` file:

```
NODE_ENV="production"

STEAM_ACCOUNT_NAME=""
STEAM_PASSWORD=""
STEAM_SHARED_SECRET=""
STEAM_IDENTITY_SECRET=""

BPTF_ACCESS_TOKEN=""
BPTF_API_KEY=""

ADMINS=["<your steamid 64>"]
KEEP=["<steamid of person to keep in friendslist>"]
ITEM_STATS_WHITELIST=[]
GROUPS=["103582791469033930"]
ALERTS=["trade", "version"]

ENABLE_SOCKET=true
CUSTOM_PRICER_URL=""
CUSTOM_PRICER_API_TOKEN=""

SKIP_BPTF_TRADEOFFERURL=true
SKIP_UPDATE_PROFILE_SETTINGS=true

TIMEZONE=""
CUSTOM_TIME_FORMAT=""
TIME_ADDITIONAL_NOTES=""

DEBUG=true
DEBUG_FILE=true

ENABLE_HTTP_API=false
HTTP_API_PORT=3001
```

### Please ensure that you have file extension viewing enabled in your Windows settings prior to continuing (click [here](https://www.howtogeek.com/205086/beginner-how-to-make-windows-show-file-extensions/) for more information).

Modify the [template.env](https://github.com/idinium96/tf2autobot/blob/master/template.env) file found in your `tf2autobot/` folder, renaming it to `.env` (yes, only a dot (`.`) and a word `env`). This file will be the file you edit when you want to configure your bot, using the below variables.

<details>
<summary>CLICK HERE IF YOU WANT TO RUN MULTIPLE BOTS ON WINDOWS</summary>

Running multiple bots on Windows is very simple. You just need to clone and build the bot again. 

You can follow these instructions:

`git clone https://github.com/TF2Autobot/tf2autobot.git <folderName>`

**Make sure to replace `<folderName>` with whatever you would like to call the folder, for example `tf2autobot2`**

`cd <folderName>`

`npm install`

`npm run build`

Now all that is left to do is to configure your [`.env`](https://github.com/TF2Autobot/tf2autobot/wiki/Configuring-the-bot#--windows) and [`options.json`](https://github.com/TF2Autobot/tf2autobot/wiki/Configure-your-options.json-file) file.
</details>

</details>

# Required Variables

To be able to start the bot, you need to set a few compulsory variables. **All of the variables in this section must be set or your bot will not run!**

If you have followed the [Before You Start](https://github.com/idinium96/tf2autobot/wiki/Before-you-start) section of the guide, you should already have your `STEAM_SHARED_SECRET` and `STEAM_IDENTITY_SECRET` on-hand.

## Bot Credentials

| Variable | Type | Description |
| :------: | :--: | ----------- |
| `STEAM_ACCOUNT_NAME` | `string` | The Steam account username of your bot account |
| `STEAM_PASSWORD` | `string` | The Steam account password of your bot account |
|  `STEAM_SHARED_SECRET`  | `string` | You can find this in the `<yourBotSteamID>.maFile` file inside the `/SDA/maFiles/` folder. Open the file using notepad and search for your `shared_secret`. An example of what that may look like is `"shared_secret": "agdgwegdgawfagxafagfkagusbuigiuefh=="` . |
| `STEAM_IDENTITY_SECRET` | `string` | Same as above (but now search for `identity_secret`). |

**Question: Where can I obtain the above secrets?**

Answer: You need to activate Steam Guard for your bot account using [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator). This application can be set up on your desktop and does not need to be set up on the system running the bot. Once SDA is fully set up, all you will need to do is transfer the secrets as described above.

## Backpack.tf User Token and API Key

If you have followed the [Before You Start](https://github.com/idinium96/tf2autobot/wiki/Before-you-start) section of the guide, you should already have your `BPTF_ACCESS_TOKEN` and `BPTF_API_KEY` on-hand.

You are able to run your bot without the User Token and API Key initially. On the first run, your bot will print out your backpack.tf User Token and API Key. You'll need to copy and paste these into your `ecosystem.json` (on Linux) or `.env` file (on Windows). Please [see this image](https://cdn.discordapp.com/attachments/697415702637838366/697820077248086126/bptf-api-token.png) for more information.

After obtaining your backpack.tf User Token and API Key, update the following variables in your configuration file:

|      Variable       |   Type   | Description                       |
| :-----------------: | :------: | --------------------------------- |
| `BPTF_ACCESS_TOKEN` | `string` | Your bot's backpack.tf User Token |
|   `BPTF_API_KEY`    | `string` | Your bot's backpack.tf API Key    |

**Question: Where can I obtain the above token/key if I am obtaining them manually from the backpack.tf?**

Answer:

-   User Token: While logged into backpack.tf as your bot account go to https://backpack.tf/connections and click `Show Token` under "User Token".
-   API Key: While still logged into backpack.tf as your bot account go to https://backpack.tf/developer/apikey/view - fill in the following for the "site URL" `http://localhost:4566/tasks` and the following for "comments" `Check if a user is banned on backpack.tf`.

## Owners' Details and Other Required Variables

| Variable | Type | Default | Description |
| :------: | :--: | :-----: | ----------- |
| `ADMINS` | `string[]` | `[""]` | The SteamID64 of your primary account (not your bot). Example: `["76561198013127982"]`. If you would like to have multiple admins, you can do the following: `["76561198013127982", "76561198077208792"]`. Any accounts in this list are designated as an admin/owner. |
|  `KEEP`  | `string[]` | `[""]` | The **same list** as `ADMINS`, **you must fill in BOTH**. Any accounts in this will not be removed from the bot's friends list in the event that its friend's list is full. |
|  `ITEM_STATS_ WHITELIST`  | `string[]` | `[]` | The SteamID64 of the people that you want to whitelist to use `!itemstats` command. By default, only IdiNium can use it on all bots (only `!itemstats` command, all other admin-only commands are not possible). Just leave it empty if you don't want to whitelist anyone, else, make sure the format is the same as in `ADMINS` or `KEEP`.|
| `GROUPS` | `string[]` | `["103582791469033930"]` | Default group is [TF2Autobot](https://steamcommunity.com/groups/TF2Autobot). If you have a Steam group, [find your group ID](https://user-images.githubusercontent.com/47635037/97783524-53a05d00-1bd3-11eb-9778-e92545f2de1e.gif) and paste it here. The bot will automatically invite new trade partners to all groups in this list (by group ID). |
| `ALERTS` | `string[]` |  `["trade", "version"]` | By default your bot will send a message/discord webhook every time a successful trade is made and send notification in Steam chat if new version has been released. To disable both, set to only `["none"]` |

## Please ensure you fill in all of the above Environmental variables.

### Additional info
 In the templates, you can see the value for `ADMINS` and `KEEP` are `["<your steamid 64>"]` and `["<steamid of person to keep in friendslist>"]`, respectively. Ensure that `<your steamid 64>` contains **YOUR SteamID64**, and that `<steamid of person to keep in friendslist>` contains the SteamID64 of anyone you don't want to be removed from the bot's friendslist.

**Question: Where can I obtain a player's SteamID64?**

Answer: You can find your SteamID64 by pasting your Steam Profile URL link to [SteamRep.com](https://steamrep.com/). Please view the gif below for more information.

![How to get SteamID64](https://user-images.githubusercontent.com/47635037/96715154-be80b580-13d5-11eb-9bd5-39613f600f6d.gif)

# Optional Variables

## Bot Profile Settings

| Variable | Type | Default | Description |
| :----: | :--: | :-----: | :---------- |
|   `SKIP_BPTF_ TRADEOFFERURL`    | `boolean` | `true`  | By default, your bot will skip the step to set it's Steam Trade Offer URL on backpack.tf. You can set this to `false` and run the bot, and if there are any issues setting this URL, please manually do so [here](https://backpack.tf/settings##general), and be sure to login using your bot's Steam account. If you've already set your Trade Offer URL on backpack.tf manually (as recommended in the guide), just leave this set to `true`. |
| `SKIP_UPDATE_ PROFILE_SETTINGS` | `boolean` | `true`  | If set to `false`, your bot will attempt to set all of your profile settings to public. This is just so that backpack.tf can load your bot inventory correctly. If you already set everything to the public, just leave this set to `true`.

## Timezone Settings

The time settings listed here will be used in the `!time` command as well as in messages sent to trade partners if their offer needs to be reviewed.

| Variable | Type | Default | Description |
| :----: | :--: | :-----: | :---------- |
|       `TIMEZONE`        | `string` |            `Europe/London`            | The timezone that you currently reside in. Please only use these [Timezone Formats](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). For example, if you live in Malaysia, you can use the value `Asia/Kuala_Lumpur`. Or if you live in New York, you can use the value `America/New_York`. |
|  `CUSTOM_TIME_FORMAT`   | `string` | `MMMM Do YYYY, HH:mm:ss ZZ` | Please refer to [this article](https://www.tutorialspoint.com/momentjs/momentjs_format.htm) for more information on specifying a custom time format for your bot. |
| `TIME_ADDITIONAL_NOTES` | `string` |            `""`             | Optional additional notes when the bot shows your current time. Some examples are your active hours or who to contact if you are offline. |

## Debug Settings

| Variable | Type | Default | Description |
| :----: | :--: | :-----: | :---------- |
|   `DEBUG`    | `boolean` | `true`  | If set to `true`, the bot will log any errors that occur into the console. |
| `DEBUG_FILE` | `boolean` | `true`  | If set to `true`, the bot will log any errors that occur to a file. This file can be later be used to create a GitHub [issue](https://github.com/idinium96/tf2autobot/issues/new/choose) to report any issues to the developers. |


## Custom Pricer Settings

Custom Pricer Settings are for directing the bot at a price source other than prices.tf. Nothing needs to be set to use
prices.tf. If you are using another price source refer to the alternative [price source's documentation](https://github.com/TF2Autobot/tf2autobot/blob/v3.2.0/src/classes/Pricer.ts#L10-L16).

| Variable | Type | Default | Description |
| :----: | :--: | :-----: | :---------- |
|      `ENABLE_SOCKET`      | `boolean`| `true`| Read: [#383](https://github.com/TF2Autobot/tf2autobot/pull/383) |
|    `CUSTOM_PRICER_URL`    | `string` | `""`  | Please leave this empty unless needed. This is unnecessary for prices.tf. |
| `CUSTOM_PRICER_API_TOKEN` | `string` | `""`  | Please leave this empty unless needed. This is unnecessary for prices.tf. |


## API

The bot can expose an HTTP server to check for availability/health or uptime.

By default is disabled, and you might turn it on in case you are [running the bot with Docker](https://github.com/TF2Autobot/tf2autobot/wiki/Running-the-bot-using-docker) and check periodically if the bot is up and running.

Keep in mind that if you run multiple instances and enable the HTTP API, you should use different `HTTP_API_PORT` values for each bot since no two bots can open the same port in the same network.

When running, you can access it from `http://127.0.0.1:[HTTP_API_PORT]`. Below you will also find the available paths for different functionalities.

| Variable | Type | Default | Description |
| :----: | :--: | :-----: | :---------- |
|     `ENABLE_HTTP_API`   | `boolean`| `false` | Read: [#413](https://github.com/TF2Autobot/tf2autobot/pull/413); Wether the API should be turned on. |
|      `HTTP_API_PORT`    | `number` | `3001` | Defaults to a non-conflicting |

Each of the following paths can be appended to the HTTP API URL.

| Endpoint | Description | Response example |
| :----: | :--: | :-----: |
| `/health` | Check for health. Returns 200 OK if the bot is running. | `OK` |
| `/uptime` | Get the current bot uptime, in seconds. | `{"uptime": 3600}` |
---

# Done?

Then the next step will be to run the bot for the first time ([Windows](https://github.com/TF2Autobot/tf2autobot/wiki/Running-the-bot-on-Windows) | [Linux](https://github.com/TF2Autobot/tf2autobot/wiki/Running-the-bot-on-Linux)) to get your [`options.json`](https://github.com/TF2Autobot/tf2autobot/wiki/Library#optionsjson-content-) generated, and then you can proceed to [configure your options.json file](https://github.com/TF2Autobot/tf2autobot/wiki/Configure-your-options.json-file)