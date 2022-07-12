⚠ To setup Discord interface for tf2autobot version of your bot must be 5.0.0 or higher ⚠

Starting at v5.0.0 it is possible for the admin to work with the bot through Discord instead of Steam chat. This page contains "how-to" information about it.


## A brief overview of the functionality

This feature adds an additional way for the admin to work with the bot. Now you can use a similar command interface not only in Steam chat, but in Discord channel as well. Commands are absolutely the same.

You will need to do several steps in order to set the thing up (detailed description below):
1. Create a Discord bot account and add the Discord bot token of it to the bot's environment file.
2. Find your Discord ID and associate it with your Steam ID in the bot's environment file.
3. Start the bot, open the Discord chat with the created discord bot account and enjoy using it!


## How to create a Discord bot account

First of all, go to [Discord developer portal](https://discord.com/developers/applications). Authorize your Discord account and create a new application. You will be asked with `NAME` when creating - type anything you want, it will then become the name of the Discord bot account you'll be chatting with. When the application is created, you will see something like this:

![Application information](https://i.imgur.com/yr4wqKo.png)

Okay, the application was created. Now go to **Bot** and there press the **Add Bot** button (and confirm it in the pop-up window). Then you will see something like this:

![Bot information](https://i.imgur.com/B4JuNih.png)

Here you have to do two important things.

1. Disable the **Public bot** setting on top. Scroll down to **Message content intent** and enable it. Press the **Save Changes** button.
![Message content intent](https://i.imgur.com/3qwN5SN.png)
2. Scroll back up and press the **Reset Token** button. Then you will _once_ be shown a token. Copy it and paste it to your environment (or ecosystem) file as `DISCORD_BOT_TOKEN`. Below goes an example with some parts censored.
![Discord bot token](https://i.imgur.com/GnxlYDN.png)

Okay, the last thing to do here is to add this Discord bot to your Discord server (assuming you have one with your webhooks). Go to **OAuth2 -> URL Generator**. Here just click the `bot` checkbox, scroll down, copy the link and paste it to your browser. There choose your Discord server and click **Authorize**. Now Discord bot account is on your server.

⚠ **WARNING** ⚠

The bot will answer only to commands from admins, but this dialogue might be visible to other people on your Discord server. Make sure to not chat with the bot on public channels. **We recommend restricting the list of readable channels** for the bot (so it can't see any messages in public channels). Also, you can use DM (right-click on the bot in the list of users, there you will see an option to start a DM chat).

![ezgif-3-17a67f58fe](https://user-images.githubusercontent.com/47635037/178523645-78ba4c7e-045c-41e6-a624-11916c51f53e.gif)

![ezgif-2-ec31d96538](https://user-images.githubusercontent.com/47635037/178480658-4363bc93-7be6-40f3-9298-3f613eff39b2.gif)

## How to find your own Discord ID

Follow this [instruction](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).


## How to integrate created Discord bot account with your bot

In the previous parts you've already found your Discord ID and inserted Discord's token into your environment file. This part is about changes of `ADMINS` parameter.

Previously, `ADMINS` parameter contained list of strings, where each string is your SteamID in the long form. Something like this: `ADMINS=["12345"]`.

Since v5.0.0 that format is wrong. Now `ADMINS` is the list of objects. Each object is enclosed in curly brackets and contains one or more key-value pairs, which separated by commas. Under the key `"steam"` you have to put your SteamID in the long string form, like before. Under the key `"discord"` you can put ID of your Discord account in the same form. Do note that `"steam"` key is required, and `"discord"` key is not (so you can continue using tf2autobot without setting up Discord UI for it).

Let's take an example. Let your Steam ID be `12345`, and your Discord ID be `67890`. Previously you had to write `ADMINS=["12345"]`. Now you can't describe it like this, but you can use any of these three forms:

* `ADMINS=[{"steam": "12345"}]`
* `ADMINS=[{"steam": "12345", "discord": null}]`
* `ADMINS=[{"steam": "12345", "discord": "67890"}]`

First two forms won't let you use Discord UI (because the bot doesn't know your Discord ID, so it won't answer to you), and the last one will. Do note that `null` value must be used without quotation marks.

And a few more words about multi-admin setup. Previously you had to list strings separated by commas (example: `ADMINS=["12345", "54321"]`). Now you have to separate objects (example: `ADMINS=[{"steam": "12345", "discord": "67890"}, {"steam": "54321", "discord": "09876"}]`. Any admin can still be limited to Steam chat (if `"discord"` key in his object is not set or set with `null` value).
