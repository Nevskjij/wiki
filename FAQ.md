# Table of Contents

- [Steam Desktop Authenticator](#steam-desktop-authenticator)
     - [Where are my account secrets?](#where-are-my-account-secrets)
     - [Decrypting and Encrypting](#decrypting-and-encrypting)
- [Trading](#trading)
	- [I set my items to bank, my bot bought one but never put it to sell. Why?](#trading)
	- [Why are my buy orders just suddenly disappearing by time?](#trading)
	- [How much does bot count a Craftable weapon as? 0.05 or 0.11 ref?](#trading)
        - [Why my bot don't accept/decline the trade automatically?](#why-my-bot-dont-acceptdecline-the-trade-automatically)

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
For your information, every time the bot bought/sold any items, it will run a check on the price list whether a listing for that item already been created or removed. When your bot did not put an item that it bought to sell, it's probably because Backpack.tf still did not fully load your items in their item server. If you see your bot backpack and the item already appeared, make sure it's not in **Using Fallback** status, or you can try to send `!refreshlist` to your bot, which your bot will execute checks on all items that it has and create sell orders for the missing items.

## Why are my buy orders just suddenly disappearing by time?
We don't have enough information regarding this issue. It could be a ratelimit with backpack.tf when your bot updating prices on a lot of items. The only way to solve this issue is by restarting your bot, or just let it recover by itself.

## How much does bot count a Craftable weapon as? 0.05 or 0.11 ref?
All craft weapons listed [here](https://github.com/idinium96/tf2autobot/blob/master/src/classes/MyHandler.ts#L3135-L3423) are counted as 0.05 ref **IF** you set [`DISABLE_CRAFTWEAPON_AS_CURRENCY`](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json#L47) as `false` and you did not add that particular item in your price list.

IF you set `DISABLE_CRAFTWEAPON_AS_CURRENCY` to `false` AND you manually add and set the price, it will not count as 0.05 ref, instead will follow your manually set prices.

IF you set `DISABLE_CRAFTWEAPON_AS_CURRENCY` to `true`, then all of that craft weapons will not be priced if you not manually set the prices.

## Why my bot don't accept/decline the trade automatically?
If someone sent an offer with wrong values, any items that are not in the pricelist, items that already reached maximum stock and etc, and `ENABLE_MANUAL_REVIEW` is set to `true`, then you should expect this to happen.

Some description of each reason:
<details><summary>🟥`_INVALID_VALUE`</summary>
<p>
The value of your side (Asked) and the trade partner side (Offered) and not equal or more. If you want to automatically decline any offer that **ONLY** has this reason, you need to set `DISABLE_AUTO_DECLINE_INVALID_VALUE` to `false`. You can also set an exceptional value for an offer with this reason to be accepted by filling the item sku(s) in the `INVALID_VALUE_EXCEPTION_SKUS` array and set the `INVALID_VALUE_EXCEPTION_VALUE_IN_REF` value. Find more about it [here](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#manual-review-settings).
</p>
</details>

<details><summary>🟦`_OVERSTOCKED`</summary>
<p>
Some of their items might already in your bot inventory and will reach or have already reached maximum stock if you accept the trade. The bot will automatically accept overstocked offers by default if the trade partner is overpaying. If you don't want this, simply set `DISABLE_ACCEPT_OVERSTOCKED_OVERPAY` to `true`. If you want your bot to automatically decline any offer that **ONLY** has this reason, you'll need to set `DISABLE_ACCEPT_OVERSTOCKED_OVERPAY` to `false`.
</p>
</details>

<details><summary>🟩`_UNDERSTOCKED`</summary>
<p>
Some of our items will be less than the minimum stock if you accept the trade (if you set the item minimum to other than 0). Your bot will automatically accept understocked offers by default if the trade partner is overpaying. If you don't want this, simply set `DISABLE_ACCEPT_UNDERSTOCKED_OVERPAY` to `true`. If you want your bot to automatically decline any offer that **ONLY** has this reason, you'll need to set `DISABLE_ACCEPT_UNDERSTOCKED_OVERPAY` to `false`.
</p>
</details>

<details><summary>🟨`_INVALID_ITEMS`</summary>
<p>
Some of the items are not in your bot price list. If you have used `tf2-automatic` before, any `INVALID_ITEMS` items will not be priced (0 keys, 0 ref value), but `TF2Autobot` will get the price of that particular item from prices.tf and price it by default. You can disable this feature by changing the `DISABLE_GIVE_PRICE_TO_INVALID_ITEMS` default value to `true`. Your bot will also accept invalid items offers by default if the trade partner is overpaying (set `DISABLE_ACCEPT_INVALID_ITEMS_OVERPAY` to `true` if you want to disable it).

Don't worry, if your bot has accepted any INVALID_ITEMS, your bot will mention you (if you enable Discord Webhook for trade summary), AND your bot will automatically add that particular item(s) to the pricelist with intent=sell (if and only if the items are priced with prices.tf).
</p>
</details>

<details><summary>🟫`_DUPED_ITEMS`</summary>
<p>
🟫`_DUPED_ITEMS`
</p>
</details>

<details><summary>🟪`_DUPE_CHECK_FAILED`</summary>
<p>
🟪`_DUPE_CHECK_FAILED`
</p>
</details>

<details><summary>⬜`_ESCROW_CHECK_FAILED`</summary>
<p>
⬜`_ESCROW_CHECK_FAILED`
</p>
</details>

<details><summary>⬜`_BANNED_CHECK_FAILED`</summary>
<p>
⬜`_BANNED_CHECK_FAILED`
</p>
</details>