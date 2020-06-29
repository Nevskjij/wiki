This page contains common errors and ways to fix them.

# Table of Contents

- [Steam Desktop Authenticator](#steam-desktop-authenticator)
     - [Where are my account secrets?](#where-are-my-account-secrets)
     - [Decrypting and Encrypting](#decrypting-and-encrypting)
- [Startup errors](#startup-errors)
   - [Missing required enviroment variable](#missing-required-enviroment-variable)
      - [ecosystem.json](#ecosystemjson)
      - [.env](#env)
   - [Unknown SteamID input format](#unknown-steamid-input-format)
   - [Access denied](#access-denied)
   - [Ratelimit exceeded](#ratelimit-exceeded)
   - [Could not get account limitations](#could-not-get-account-limitations)
   - [Unexpected token in JSON](#unexpected-token-in-json)
   - [Reason: Failed to accept mobile confirmation.](#reason-failed-to-accept-mobile-confirmation)
   
# Steam Desktop Authenticator
Steam Desktop Authenticator is a a desktop implementation of Steam's mobile authenticator app. Which you can use if you for example do not have a phone, or if you need easy access to your account secrets for a bot account.  
You can download it [here](https://github.com/Jessecar96/SteamDesktopAuthenticator)  

### Where are my account secrets?
You can find your `shared_secret` and `identity_secret` by going to your Steam Desktop Authenticator folder, then into the `maFiles` folder. Here you will find  account files. Find the one with your steamID and open it.  
If you are unable to read anything, your file is likely encrypted. Check out [Decrypting and Encrypting](#decryptingandencrypting) below.  
If it is not encrypted, simply copy and paste the `shared_secret` and `identity_secret` into your bots `ecosystem.json` or `.env` file. Depends on which one you are using.  

### Decrypting and Encrypting
If your file is encrypted, meaning the contents probably look something like `AJHSASJLDHASKLJHD87ASDASLNJ3S...`, you can decrypt it by opening Steam Desktop Authenticator, clicking `Setup Encryption` on the top right, entering your passkey and then click `Accept` 2 more times, without entering in a new passkey.  
Now re-open your maFile. You should be able to get your secrets now.  

# Startup errors
### Missing required enviroment variable
When updating your enviromental variables, almost make sure you restart the bot with the `--update-env` option if you are using PM2. As explained [here](https://github.com/Nicklason/tf2-automatic/wiki/PM2#updating-environment-variables) 
##### ecosystem.json
You need to make sure your file is **NOT** called `ecosystem.template.json`. It needs to be `ecosystem.json`.  

##### .env
Before trying to fix this error, you should [enable viewing file extensions](https://fileinfo.com/help/windows_10_show_file_extensions).  
MAKE SURE THE FILE IS NOT CALLED `config.env` OR `bot.env` OR ANYTHING. JUST `.env`.  
If your computer does not allow you to name it `.env`, simply call it `.env.` (with the extra `.`).

### Unknown SteamID input format
In your `.env` or `ecosystem.json`, the `ADMINS` and `KEEP` options need to have valid SteamID64's in them. For example: `76561198144346135` is a valid SteamID64.  
You can find this on [SteamRep](https://steamrep.com/) or on your [Backpack.tf profile](https://backpack.tf/my)

### Access denied
Your Steam account(s) needs to be [unlimited](https://support.steampowered.com/kb_article.php?ref=3330-IAGK-7663). To make your Steam account(s) unlimited you need to add $5 or more to the Steam account(s) [here](https://store.steampowered.com/steamaccount/addfunds) (remember to be logged into the bot(s)' account). If you're using another currency than USD, you might need to add more than $5 due to conversion rates.

### Ratelimit Exceeded
You have logged in too many times (possibly due to it crashing and restarting too often). Stop the bot for an hour and then start it again.

### Could not get account limitations
As it says in the console with the message about the error, set `SKIP_ACCOUNT_LIMITATIONS` to `true` in your `.env` or `ecosystem.json`.

### Unexpected token in JSON
There are multiple cases where this may happen. If your error looks somewhat like this: ![https://i.imgur.com/mKMp3i5.png](https://i.imgur.com/mKMp3i5.png "error")  
Then something went wrong with your `polldata.json` file. This is located in the `tf2-automatic/files/{your steamid}/` folder. Simply deleting it will fix the issue.

If this issue is not solved by deleting your `polldata.json` file, check your `pricelist.json` file for corruption. Making a regular backup of your `pricelist.json` file is always recommended.

If the error is bigger, and starts with 
```cmd
SyntaxError: Unexpected token o in JSON at position 1
    at JSON.parse (<anonymous>)
    at new Bot (C:\Users\Name\Desktop\Edited\dist\classes\Bot.js:74:72)
```
Or something similar, then you did not set your `ALERTS` properly in your `.env` or `ecosystem.json`.  
It is supposed to look like `["trade"]` or `["none"]`. This error usually happens if you forget the `[]` brackets.

### Reason Failed to accept mobile confirmation
The bot may produce this error when a user attempts to trade using the !buy or !sell commands.  
This issue occurs when SDA is left open. Please close SDA.