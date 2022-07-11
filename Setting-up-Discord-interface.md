⚠ To setup Discord interface for tf2autobot version of your bot must be 5.0.0 or higher ⚠

Starting at v5.0.0 it is possible for admin to work with the bot through Discord instead of Steam chat. This page contains "how-to" information about it.


## A brief overview of the functionality

This feature adds additional way for admin to work with the bot. Now you can use similar command interface not only in Steam chat, but in Discord channel as well. Commands are absolutely the same.

You will need to do several steps in order to set the thing up (detailed description below):
1. Create a Discord bot account and add api token of it to the bot's environment file.
2. Find your Discord ID and associate it with your Steam ID in the bot's environment file.
3. Start the bot, open the Discord chat with the created discord bot account and enjoy using it!


## How to create Discord bot account

First of all, go to [Discord developer portal](https://discord.com/developers/applications). Authorize with _your_ account and create a new application. You will be asked with `NAME` when creating - type anything you want, it will then become the name of Discord bot account you'll be chatting with. When the application created, you will see something like this:

![Application information](https://i.imgur.com/yr4wqKo.png)

Okay, the application was created. Now go to **Bot** and there press **Add Bot** button (and confirm it in the pop-up window). Then you will see something like this:

![Bot information](https://i.imgur.com/B4JuNih.png)

Here you have to do two important things.

1. Disable **Public bot** setting on top. Scroll down to **Message content intent** and enable it. Press **Save Changes** button.
![Message content intent](https://i.imgur.com/3qwN5SN.png)
2. Scroll back up and press **Reset Token** button. Then you will _once_ be shown with a token. Copy it and paste to your environment (or ecosystem) file as `DISCORD_BOT_TOKEN`. Below goes an example with some parts censored.
![Discord bot token](https://i.imgur.com/XEGrn6G.png)

Okay, the last thing to do here is to add this Discord bot to your Discord server (assuming you have one with your webhooks). Go to **OAuth2 -> URL Generator**. Here just click the `bot` checkbox, scroll down, copy the link and paste it to your browser. There choose your Discord server and click **Authorize**. Now Discord bot account is in your server.

⚠ **WARNING** ⚠

Bot will answer only to commands from admins, but this dialog might be visible to other people in your Discord server. Make sure to not chat with the bot in public channels. We recommend to restrict the list of readable channels for the bot (so it can't see any messages in public channels). Also you can use DM (right-click on the bot in the list of users, there you will see an option to start a DM chat).
