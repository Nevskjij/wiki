# Table of Contents

- [Steam Desktop Authenticator](#steam-desktop-authenticator)
     - [Where are my account secrets?](#where-are-my-account-secrets)
     - [Decrypting and Encrypting](#decrypting-and-encrypting)
- [Trading](#trading)
	- [I set my items to bank, my bot bought one but never put it to sell. Why?](#trading)
	- [Why are my buy orders just suddenly disappearing by time?](#trading)
	- [How much does bot count a Craftable weapon as? 0.05 or 0.11 ref?](#trading)

# Steam Desktop Authenticator
Steam Desktop Authenticator is a desktop implementation of Steam's mobile authenticator app. Which you can use if you for example do not have a phone, or if you need easy access to your account secrets for a bot account.  
You can download it [here](https://github.com/Jessecar96/SteamDesktopAuthenticator)  

## Where are my account secrets?
You can find your `shared_secret` and `identity_secret` by going to your Steam Desktop Authenticator folder, then into the `maFiles` folder. Here you will find account files. Find the one with your steamID and open it.  
If you are unable to read anything, your file is likely encrypted. Check out [Decrypting and Encrypting](#decryptingandencrypting) below.  
If it is not encrypted, simply copy and paste the `shared_secret` and `identity_secret` into your bots `ecosystem.json` or `.env` file. Depends on which one you are using.  

## Decrypting and Encrypting
If your file is encrypted, meaning the contents probably look something like `AJHSASJLDHASKLJHD87ASDASLNJ3S...`, you can decrypt it by opening Steam Desktop Authenticator, clicking `Setup Encryption` on the top right, enter your passkey and then click `Accept` 2 more times, without entering in a new passkey.  
Now re-open your maFile. You should be able to get your secrets now.

# Trading

## I set my items to bank, my bot bought one but never put it to sell. Why?
For your information, every time the bot bought/sold any items, it will run a check on the pricelist whether a listing for that item already been created or removed. When your bot did not put an item that it bought to sell, it's probably because Backpack.tf still did not fully load your items in their item server. If you see your bot backpack and the item already appeared, make sure it's not in **Using Fallback** status, or you can try to send `!refreshlist` to your bot, which your bot will execute checks on all items that it has and create sell orders for the missing items.

## Why are my buy orders just suddenly disappearing by time?
We don't have enough information regarding this issue. It could be a ratelimit with backpack.tf when your bot updating prices on a lot of items. The only way to solve this issue is by restarting your bot, or just let it recover by itself.

## How much does bot count a Craftable weapon as? 0.05 or 0.11 ref?
All craft weapons listed [here](https://github.com/idinium96/tf2autobot/blob/master/src/classes/MyHandler.ts#L3135-L3423) are counted as 0.05 ref **IF** you set [`DISABLE_CRAFTWEAPON_AS_CURRENCY`](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json#L47) as `false` and you did not add that particular item in your pricelist.

IF you set `DISABLE_CRAFTWEAPON_AS_CURRENCY` to `false` AND you manually add and set the price, it will not count as 0.05 ref, instead will follow your manually set prices.

IF you set `DISABLE_CRAFTWEAPON_AS_CURRENCY` to `true`, then all of that craft weapons will not be priced if you not manually set the prices.