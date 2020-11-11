## Difference between TF2Autobot and tf2-automatic

TF2Autobot adds advantageous features on top of the original features in the tf2-automatic repository. Let me list some notable features in the original tf2-automatic and some that have been added in TF2Autobot:

### Original tf2-automatic

-   free auto pricing (using prices from [prices.tf](https://prices.tf/)) and unlimited listings (only limited by your backpack.tf listings cap).
-   automatically craft/smelt pure metal (to maintain supply in all metal types).
-   dupe check on items that are more than a certain amount of keys (you decide/set the number of keys).
-   trade offer review (if you were offered an invalid value/item, the item is overstocked, or the item is duped).

### TF2Autobot version

-   **Discord Webhook:**
    -   use Discord Webhooks for your bot to send accepted trade summaries, pending trade offer reviews, and/or private messages to a Discord server.
    -   disable mention owner on pending trade offers with `INVALID_VALUE`.
-   **Autokeys:**
    -   enable Autokeys (to maintain ample refined metal stock) and key banking.
-   **Manual review:**
    -   send the trade partner a summary of their offer if it needs to be reviewed.
    -   automatically accept trades that underpay by a certain amount of refined with `INVALID_VALUE exception` (you decide/set the amount of refined and can be enabled only for certain item qualities).
    -   automatically decline (skip manual review) **ONLY** `INVALID_VALUE` trade (if it does not meet the set requirements for `INVALID_VALUE exception`).
    -   automatically accept (skip manual review) `INVALID_ITEMS` or `OVERSTOCKED` trades if the trade partner offers to overpay (will mention owner on Discord Webhook).
    -   new `UNDERSTOCKED` reason for manual review.
    -   option to automatically decline `OVERSTOCKED` or `UNDERSTOCKED` reason.
    -   list all reasons and items for each trade offer review.
-   **Support craft weapons as currency:**
    -   set craft weapons as currency (0.05 ref) and automatically craft duplicated craftable weapons and matched class weapons into metal (if not in pricelist).
-   **Option to only accept full uses items:**
    -   Dueling Mini-Game check - only accept 5 Uses!
    -   Noise Maker check - only accept 25 Uses!
-   **Custom Listing Note:**
    -   set custom buy or sell order listing note for any item of your choice!
-   **Items Grouping in pricelist:**
    -   set a group for specific items in your pricelist so it will be easy to manage, such as if you only want to update `intent=bank` to `intent=sell` to only "craftHats" items group!
-   **Customs:**
    -   set your own custom greeting, success/failed messages, and/or trade offer review notes.
    -   set your custom playing game name.
    -   option to only play Team Fortress 2.
    -   disable "show only metal" in the trade summary (it will show x keys, y ref instead of just x ref on the original version).
    -   option to disable accept friend requests and disable invite people to join Steam groups.
    -   option to recognize Strange Unusual as usual Unusual and vice versa.
    -   option to recognize Festivized items as non-Festivized.
-   **Improvements:**
    -   request price check to prices.tf after every successful trade on each item involved in the trade (except craft weapons and pure).
    -   option to request for `INVALID_ITEMS` (items that are not in your pricelist) to be priced by Prices.TF.
    -   automatically add accepted `INVALID_ITEMS` to the pricelist (if priced with prices.tf and not from ADMINS) with autoprice set to true and intent to sell, which when sold, will be automatically removed.
    -   notify the owner if someone traded high valued items (spelled and/or strange parts).
    -   use the infinity symbol (∞) for infinite stock (maximum set to -1).
    -   able to create **sell** orders for specific Mann Co. Supply Crate, Mann Co. Supply Munition and, Salvaged Mann Co. Supply Crate series and Skins/War Paint!
-   **Others:**
-   emojis on almost all messages.
-   newly added commands: "!pure", "!time", "!delete", "!check", "!block", "!unblock", "!autokeys", "!refreshautokeys", "!refreshlist", "!find", "!inventory", and more!

More info in the [Releases](https://github.com/idinium96/tf2autobot/releases) note pages.

## Added features

### Discord Webhook feature

Instead of your bot sending trade summaries, trade offer reviews, and messages to you via Steam Chat, your bot is able to send it to different channels in your Discord server!
If you want to interact with the trade offer reviews and messages sent by your Discord Webhook, you must install [tf2-autocord](https://github.com/idinium96/tf2-autocord).

Screenshots:

-   Trade summary (or live-trades) -

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/89725250-1434fb00-da40-11ea-8ccc-8755b1af89c6.PNG" alt="trade-summary" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Offer review (when trade partner sent wrong value/overstocked/etc) -

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/85020166-80168800-b1a2-11ea-99f2-04766677fdf7.PNG" alt="Offer-review" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Messages (when the trade partner uses "!message" command -

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581313-9cb56780-ae12-11ea-9dcf-2d660d8ae184.PNG" alt="Messages" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Price update (Discord Only) - Show the price changes for each item on your pricelist -

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/83712639-cc1ce500-a658-11ea-855d-5de43b39ff2f.png" alt="price-update" style="display:block;margin-left:auto;margin-right:auto;"></div>

You can also set it to send only the trade summary via Discord and have others (like Offer review and Messages) still sent to you via Steam Chat.

Note: it's also an option to show key rate/pure stock/quick links on each Webhook message.

If you want to use this feature, you must use the [ecosystem.template.json](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json) from this version. It contains many more variables for you to fill in.

### Autokeys (auto-buy or sell keys) feature

When this feature is enabled, your bot will automatically buy or sell keys depending on the amount of pure your bot currently has. You'll need to set your minimum/maximum keys and minimum/maximum refined metals in your ecosystem.json. Additional explanation can be found [here](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#autokeys-feature).

```
.____________________________________________________________.  ._______________________________.
|       **Buying Keys**       |       **Selling Keys**       |  |       **Banking Keys**        |
|       ***************       |       ****************       |  |       ****************        |
|        <———————————○        |            ○————————————>    |  |            ○————————————>     |
| Keys -----|--------|----->  |  Keys -----|--------|----->  |  |  Keys -----|--------|----->   |_______________________________.
|                    ○———>    |         <——○                 |  |            ○————————○         |          **Disabled**         |
| Refs -----|--------|----->  |  Refs -----|--------|----->  |  |  Refs -----|--------|----->   |          ************         |
|          min      max       |           min      max       |  |           min      max        |         <——●                  |
|_____________________________|______________________________|  |______________________________.|  Keys -----|--------|----->   |
                |         **Disabled**        |                 |    **Buying when more ref**   |         <———————————●         |
                |         ************        |                 |          ************         |  Refs -----|--------|----->   |
                |        <——●————————●···>    |                 |         <——●                  |           min      max        |
                | Keys -----|--------|----->  |                 |  Keys -----|--------|----->   |_______________________________|
                |           ●————————●···>    |                 |            ○————————————>     |
                | Refs -----|--------|----->  |                 |  Refs -----|--------|----->   |
                |          min      max       |                 |           min      max        |
                |_____________________________|                 |_______________________________|
```

Some screenshots:

-   When your bot has enough keys to sell (when your ref < minimum) OR enough ref to buy more keys (when your ref > maximum and keys < max):

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581306-9a530d80-ae12-11ea-9bd5-3a988ac447d9.png" alt="autokeys1" style="display:block;margin-left:auto;margin-right:auto;"></div>

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581309-9b843a80-ae12-11ea-8374-0f7d3c631fa6.png" alt="autokeys2" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   When your bot doesn't have enough keys to sell, Autokeys will not be active:

      <div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581310-9c1cd100-ae12-11ea-80fa-085ad8bff73e.png" alt="autokeys3" style="display:block;margin-left:auto;margin-right:auto;"></div>

You can see the code of this feature [here](https://github.com/idinium96/tf2autobot/blob/master/src/classes/Autokeys.ts).

### Emojis and more commands added

#### Admin commands

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/92323077-5d409500-f068-11ea-8d44-4a6a127fbb10.png" alt="newlook-command-admin" style="display:block;margin-left:auto;margin-right:auto;"></div>

#### Trade partner commands

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/89725439-244dda00-da42-11ea-9ea8-f3e159c19cea.png" alt="newlook-command-partner" style="display:block;margin-left:auto;margin-right:auto;"></div>

### Offer review summary on the trade partner side

![review-note-trade-partner](https://user-images.githubusercontent.com/47635037/85020170-8147b500-b1a2-11ea-96b5-1805ad8cc31c.PNG)

### INVALID_VALUE exception

If you're having your bot trade  Unusuals or Australiums (which the value, as we know, is more than 5 keys), and someone sends a trade offer with 0.11 ref underpay, your bot will skip this offer and send you a notification to review this offer. With this exception, your bot will accept the trade as long as the underpay is less than the exceptional value that you've set. To use this feature, you'll need to set the exception value on both `INVALID_VALUE_EXCEPTION_SKUS` and `INVALID_VALUE_EXCEPTION_VALUE_IN_REF`. See [here](https://github.com/idinium96/tf2autobot/wiki/Configuring-the-bot-using-the-environment-file#manual-review-settings).

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84966884-38adde80-b145-11ea-9aac-d28daf9a74e6.PNG" alt="Invalid_value_exception2" style="display:block;margin-left:auto;margin-right:auto;width:540px;height:450px;"></div>

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84966887-39df0b80-b145-11ea-9d81-021d302e7cf0.PNG" alt="Invalid_value_exception2" style="display:block;margin-left:auto;margin-right:auto;"></div>