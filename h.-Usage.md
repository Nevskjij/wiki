# a. Add item to pricelist

In order to have your bot to start trading, you will need to tell your bot what items to buy/sell/bank by adding the items to the pricelist through Steam Chat.
The command that you will use is **!add**.

## a.1 - Item identifying parameter

You have 3 choices of item identifying parameters on how you want to add your items:

1. `name` - Must be the item based name (without any quality/effect/Killstreak and etc)
2. `defindex` - The item definition index. You can find it [here](https://wiki.alliedmods.net/Team_Fortress_2_Item_Definition_Indexes) or [here](https://docs.google.com/spreadsheets/d/11bv5J-l1UCNjvTF2FyiqivbQds8LxBCQj0QBpw6Ukec/edit#gid=0)
3. `sku` **(recommended)** - The item "Stock Keeping Unit".

## a.1.1 - `name` and `defindex` parameters

These two parameters act the same since the defindex (in integer form) is just a replacement for the name of an item (if the bot failed need more specific detail of an item). There are 6 _optional_ sub-parameters under these two item identifying parameters:

|  Parameter   | Default  | Description                                                                                                                     |
| :----------: | :------: | :------------------------------------------------------------------------------------------------------------------------------ |
| `craftable`  |  `true`  | Set to `false` if you want the item to be a Non-Craftable.                                                                      |
|  `quality`   | `Unique` | Normal/Genuine/Vintage/Unusual/Unique/Community/Valve/Self-made/Strange/Haunted/Collector's/Decorated (this is case sensitive). |
| `australium` | `false`  | Set to `true` if you want that item to be an Australium (Australium-able weapons only).                                         |
|   `effect`   |  `null`  | An Unusual effect name, for example: `Sunbeams` or `Green Confetti`.                                                            |
| `killstreak` |   `0`    | This should be in integer of 1 to 3 only. 1 - Killstreak, 2 - Specialized Killstreak and 3 - Professional Killstreak.           |
|  `festive`   | `false`  | `true` or `false`.                                                                                                              |
|  `paintkit`  |  `null`  | When adding a decorated weapon/skin. This should be the War Paint name (broken).                                                |

Example:

-   Tour of Duty Ticket:
    -   `!add name=Tour of Duty Ticket` OR 
    -   `!add defindex=725` (no need to add sub-parameter since this is the default).
-   Non-Craftable Tour of Duty Ticket:
    -   `!add name=Tour of Duty Ticket&craftable=false` OR
    -   `!add defindex=725&craftable=false`
-   Vintage Pyro's Beanie:
    -   `!add name=Pyro's Beanie&quality=Vintage` OR
    -   `!add defindex=51&quality=Vintage`
-   Strange Silver Botkiller Minigun Mk.II:
    -   `!add name=Silver Botkiller Minigun Mk.II&quality=Strange` OR
    -   `!add defindex=958&quality=Strange`
-   Pyroland Daydream Smissmas Saxton:
    -   `!add name=Smissmas Saxton&quality=Unusual&effect=Pyroland Daydream` OR
    -   `!add defindex=31089&quality=Unusual&effect=Pyroland Daydream`
-   Strange Australium Tomislav:
    -   `!add name=Tomislav&quality=Strange&australium=true` OR
    -   `!add defindex=424&quality=Strange&australium=true`
-   Strange Festivized Australium Tomislav:
    -   `!add name=Tomislav&quality=Strange&australium=true&festive=true` OR
    -   `!add defindex=424&quality=Strange&australium=true&festive=true`
-   Strange Professional Killstreak Australium Tomislav:
    -   `!add name=Tomislav&quality=Strange&australium=true&killstreak=3` OR
    -   `!add defindex=424&quality=Strange&australium=true&killstreak=3`
-   Festive Black Box:
    -   `!add name=Festive Black Box` OR
    -   `!add defindex=1085`

\*Notes:

-   If you want to add **Mann Co. Supply Crate Key** with name parameter, it will list out all possible key defindexes. Please choose the one at top with the name **Decoder Ring** and use `!add defindex=5021`.
-   Festive and Festivized are two different things. When adding a Festive weapon, please include `Festive` in the item name, but if `Festivized`, you need to add sub-parameter `festive=true`.

## a.1.2 - `sku` parameter

This parameter is recommended because you will no longer need to use the sub-parameters in a.1 table.
So how can I find the sku of a specific item?

-   Go to [Marketplace.tf](https://marketplace.tf/).
-   In the search bar, type in the item name or unusual effect or anything related.
-   If "No items found", simply click on the "In stock" button two to the right of the search bar and it will change to "Not In Stock".
-   If your desired item appeared, click on it and take a look on the URL. The item sku is right at the end of the URL.

Example 1:

-   Item: Sunbeams Cosa Nostra Cap
-   URL: https://marketplace.tf/items/tf2/459;5;u17
-   `sku`: 459;5;u17
-   to add: `!add sku=459;5;u17`

Example 2:

-   Item: Specialized Festivized Australium Tomislav
-   URL: https://marketplace.tf/items/tf2/424;11;australium;kt-2;festive
-   `sku`: 424;11;australium;kt-2;festive
-   to add: `!add sku=424;11;australium;kt-2;festive`
