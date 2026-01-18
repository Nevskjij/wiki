# Table of content

- [Options.json content](#optionsjson-content-)
- [Strange Parts](#strange-parts-excluding-built-in-parts-)
- [Paints](#paints-)
- [Crates/Cases](#cratescases-)
- [Sheens](#sheens-)
- [Killstreakers](#killstreakers-)
- [Spells](#spells-)
- [Default message/reply](#default-messagereply-)
    - [Auto Decline reply](#--auto-decline-reply-)
    - [Declined with other reasons](#--declined-with-other-reasons-)
    - [Accepted message](#--accepted-message-)
        - [Automatic](#-automatic-)
        - [Manual](#-manual-)
- [Gift words](#gift-words-)

# Options.json content [^](#table-of-content)

Refer: https://github.com/TF2-Price-DB/tf2autobot-pricedb/blob/master/.example/options.json

# Strange Parts (Excluding built-in parts) [^](#table-of-content)

```js
{
    // "Description Name": "Partial SKU"       Defindex
    "Scouts Killed": "sp10", //                  6003
    "Snipers Killed": "sp11", //                 6005
    "Soldiers Killed": "sp12", //                6002
    "Demomen Killed": "sp13", //                 6001
    "Heavies Killed": "sp14", //                 6000
    "Pyros Killed": "sp15", //                   6006
    "Spies Killed": "sp16", //                   6008
    "Engineers Killed": "sp17", //               6004
    "Medics Killed": "sp18", //                  6007
    "Buildings Destroyed": "sp19", //            6009
    "Projectiles Reflected": "sp20", //          6010
    "Headshot Kills": "sp21", //                 6011
    "Airborne Enemy Kills": "sp22", //           6012
    "Gib Kills": "sp23", //                      6013
    "Kills Under A Full Moon": "sp27", //        6015
    "Dominations": "sp28", //                    6016
    "Revenges": "sp30", //                       6018
    "Posthumous Kills": "sp31", //               6019
    "Teammates Extinguished": "sp32", //         6020
    "Critical Kills": "sp33", //                 6021
    "Kills While Explosive-Jumping": "sp34", //  6022
    "Sappers Removed": "sp36", //                6025
    "Cloaked Spies Killed": "sp37", //           6024
    "Medics Killed That Have Full ÜberCharge": "sp38", // 6023
    "Robots Destroyed": "sp39", //               6026
    "Giant Robots Destroyed": "sp40", //         6028
    "Kills While Low Health": "sp44", //         6032
    "Kills During Halloween": "sp45", //         6033
    "Robots Killed During Halloween": "sp46", // 6034
    "Defenders Killed": "sp47", //               6035
    "Submerged Enemy Kills": "sp48", //          6036
    "Kills While Invuln ÜberCharged": "sp49", // 6037
    "Tanks Destroyed": "sp61", //                6038
    "Long-Distance Kills": "sp62", //            6039
    "Kills During Victory Time": "sp67", //      6041
    "Robot Scouts Destroyed": "sp68", //         6042
    "Robot Spies Destroyed": "sp74", //          6048
    "Taunt Kills": "sp77", //                    6051
    "Unusual-Wearing Player Kills": "sp78", //   6052
    "Burning Player Kills": "sp79", //           6053
    "Killstreaks Ended": "sp80", //              6054
    "Freezecam Taunt Appearances": "sp81", //    6055
    "Damage Dealt": "sp82", //                   6056
    "Fires Survived": "sp83", //                 6057
    "Allied Healing Done": "sp84", //            6058
    "Point Blank Kills": "sp85", //              6059
    "Kills": "sp87", //                          6060
    "Full Health Kills": "sp88", //              6061
    "Taunting Player Kills": "sp89", //          6062
    "Not Crit nor MiniCrit Kills": "sp93", //    6063
    "Players Hit": "sp94", //                    6064
    "Assists": "sp95", //                        6065
}
```

# Paints [^](#table-of-content)

```json
{
    "A Color Similar to Slate": "p3100495",
    "A Deep Commitment to Purple": "p8208497",
    "A Distinctive Lack of Hue": "p1315860",
    "A Mann's Mint": "p12377523",
    "After Eight": "p2960676",
    "Aged Moustache Grey": "p8289918",
    "An Extraordinary Abundance of Tinge": "p15132390",
    "Australium Gold": "p15185211",
    "Color No. 216-190-216": "p14204632",
    "Dark Salmon Injustice": "p15308410",
    "Drably Olive": "p8421376",
    "Indubitably Green": "p7511618",
    "Mann Co. Orange": "p13595446",
    "Muskelmannbraun": "p10843461",
    "Noble Hatter's Violet": "p5322826",
    "Peculiarly Drab Tincture": "p12955537",
    "Pink as Hell": "p16738740",
    "Radigan Conagher Brown": "p6901050",
    "The Bitter Taste of Defeat and Lime": "p3329330",
    "The Color of a Gentlemann's Business Pants": "p15787660",
    "Ye Olde Rustic Colour": "p8154199",
    "Zepheniah's Greed": "p4345659",
    "An Air of Debonair": "p6637376",
    "Balaclavas Are Forever": "p3874595",
    "Cream Spirit": "p12807213",
    "Operator's Overalls": "p4732984",
    "Team Spirit": "p12073019",
    "The Value of Teamwork": "p8400928",
    "Waterlogged Lab Coat": "p11049612"
}
```

# Crates/Cases [^](#table-of-content)

## - Crates

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/106851775-d31d5b00-66f1-11eb-873c-4692fbd7fada.png" alt="listings" style="display: block; margin-left: auto; margin-right: auto;"></div>

## - Cases

```json
{
    "Festive Winter Crate #6": "5048;6;c6",
    "Refreshing Summer Cooler #22": "5066;6;c22",
    "Naughty Winter Crate #35": "5070;6;c35",
    "Nice Winter Crate #36": "5071;6;36",
    "Scorched Crate #46": "5078;6;c46",
    "Fall Crate #48": "5080;6;c48",
    "Eerie Crate #51": "5627;6;c51",
    "Naughty Winter Crate 2012 #52": "5629;6;c52",
    "Nice Winter Crate 2012 #53": "5630;6;c53",
    "Robo Community Crate #58": "5635;6;c58",
    "Select Reserve Mann Co. Supply Crate #60": "5660;6;c60",
    "Summer Appetizer Crate #61": "5640;6;c61",
    "Red Summer 2013 Cooler #62": "5642;6;c62",
    "Orange Summer 2013 Cooler #63": "5644;6;c63",
    "Yellow Summer 2013 Cooler #64": "5646;6;c64",
    "Green Summer 2013 Cooler #65": "5648;6;c65",
    "Aqua Summer 2013 Cooler #66": "5650;6;c66",
    "Blue Summer 2013 Cooler #67": "5652;6;c67",
    "Brown Summer 2013 Cooler #68": "5654;6;c68",
    "Black Summer 2013 Cooler #69": "5656;6;c69",
    "Fall 2013 Acorns Crate #72": "5708;6;c72",
    "Fall 2013 Gourd Crate #73": "5709;6;c73",
    "Spooky Crate #74": "5712;6;c74",
    "Naughty Winter Crate 2013 #78": "5714;6;c78",
    "Nice Winter Crate 2013 #79": "5715;6;c79",
    "Mann Co. Strongbox #81": "5719;6;c81",
    "Mann Co. Munition Crate #82": "5734;6;c82",
    "Mann Co. Munition Crate #83": "5735;6;c83",
    "Mann Co. Munition Crate #84": "5742;6;c84",
    "Mann Co. Munition Crate #85": "5752;6;c85",
    "Limited Late Summer Crate #86": "5761;6;c86",
    "End of the Line Community Crate #87": "5774;6;c87",
    "Naughty Winter Crate 2014 #88": "5789;6;c88",
    "Nice Winter Crate 2014 #89": "5790;6;c89",
    "Mann Co. Munition Crate #90": "5781;6;c90",
    "Mann Co. Munition Crate #91": "5802;6;c91",
    "Mann Co. Munition Crate #92": "5803;6;c92",
    "The Concealed Killer Weapons Case #93": "5806;6;c93",
    "The Powerhouse Weapons Case #94": "5807;6;c94",
    "Gun Mettle Cosmetic Case #95": "5817;6;c95",
    "Quarantined Collection Case #96": "5822;6;c96",
    "Confidential Collection Case #97": "5823;6;c97",
    "Gargoyle Case #98": "5828;6;c98",
    "Pyroland Weapons Case #99": "5831;6;c99",
    "Warbird Weapons Case #100": "5832;6;c100",
    "Tough Break Cosmetic Case #101": "5842;6;c101",
    "Mayflower Cosmetic Case #102": "5849;6;c102",
    "Mann Co. Munition Crate #103": "5859;6;c103",
    "Creepy Crawly Case #104": "5861;6;c104",
    "Unlocked Winter 2016 Cosmetic Case #105": "5865;6;c105",
    "Rainy Day Cosmetic Case #106": "5867;6;c106",
    "Abominable Cosmetic Case #107": "5871;6;c107",
    "Unleash the Beast Cosmetic Case #108": "5875;6;c108",
    "Jungle Jackpot War Paint Case #109": "5883;6;c109",
    "Infernal Reward War Paint Case #110": "5885;6;c110",
    "'Decorated War Hero' War Paint\nCivilian Grade Keyless Case": "18000;6;c111",
    "'Decorated War Hero' War Paint\nFreelance Grade Keyless Case": "18001;6;c112",
    "'Decorated War Hero' War Paint\nMercenary Grade Keyless Case": "18002;6;c113",
    "'Contract Campaigner' War Paint\nCivilian Grade Keyless Case": "18003;6;c114",
    "'Contract Campaigner' War Paint\nFreelance Grade Keyless Case": "18004;6;c115",
    "'Contract Campaigner' War Paint\nMercenary Grade Keyless Case": "18005;6;c116",
    "Winter 2017 Cosmetic Case #117": "5888;6;c117",
    "Winter 2017 War Paint Case #118": "5890;6;c118",
    "Blue Moon Cosmetic Case #119": "5893;6;c119",
    "Violet Vermin Case #120": "5894;6;c120",
    "Scream Fortress X War Paint Case #121": "5897;6;c121",
    "Winter 2018 Cosmetic Case #122": "5902;6;c122",
    "Summer 2019 Cosmetic Case #123": "5904;6;c123",
    "Spooky Spoils Case #124": "5905;6;c124",
    "Winter 2019 Cosmetic Case #125": "5909;6;c125",
    "Winter 2019 War Paint Case #126": "5912;6;c126",
    "Summer 2020 Cosmetic Case #127": "5914;6;c127",
    "Wicked Windfall Case #128": "5915;6;c128",
    "Scream Fortress XII War Paint Case #129": "5918;6;c129",
    "Winter 2020 Cosmetic Case #130": "5922;6;c130",
    "Winter 2020 War Paint Case #131": "5925;6;c131",
    "Summer 2021 Cosmetic Case #132": "5927;6;c132",
    "Crimson Cache Case #133": "5928;6;c133",
    "Scream Fortress XIII War Paint Case #134": "5931;6;c134",
    "Winter 2021 Cosmetic Case #135": "5935;6;c135",
    "Summer 2022 Cosmetic Case #136": "5938;6;c136",
    "Ghoulish Gains Case #137": "5939;6;c137",
    "Scream Fortress XIV War Paint Case #138": "5942;6;c138",
    "Winter 2022 Cosmetic Case #139": "5947;6;c139"
}
```

# Sheens [^](#table-of-content)

```json
{
    "Team Shine": "ks-1",
    "Deadly Daffodil": "ks-2",
    "Manndarin": "ks-3",
    "Mean Green": "ks-4",
    "Agonizing Emerald": "ks-5",
    "Villainous Violet": "ks-6",
    "Hot Rod": "ks-7"
}
```

# Killstreakers [^](#table-of-content)

```json
{
    "Fire Horns": "ke-2002",
    "Cerebral Discharge": "ke-2003",
    "Tornado": "ke-2004",
    "Flames": "ke-2005",
    "Singularity": "ke-2006",
    "Incinerator": "ke-2007",
    "Hypno-Beam": "ke-2008"
}
```

# Spells [^](#table-of-content)

```json
{
    "Team Spirit Footprints": "s-1000",
    "Gangreen Footprints": "s-1001",
    "Corpse Gray Footprints": "s-1002",
    "Violent Violet Footprints": "s-1003",
    "Rotten Orange Footprints": "s-1004",
    "Bruised Purple Footprints": "s-1005",
    "Headless Horseshoes": "s-1006",
    "Putrescent Pigmentation": "s-2000",
    "Die Job": "s-2001",
    "Chromatic Corruption": "s-2002",
    "Spectral Spectrum": "s-2003",
    "Sinister Staining": "s-2004",
    "Voices From Below": "s-3000",
    "Exorcism": "s-4000",
    "Pumpkin Bombs": "s-5000",
    "Halloween Fire": "s-6000"
}
```

# Default message/reply [^](#table-of-content)

## - Auto Decline reply [^](#table-of-content)

| Reason | Default |
| :--: | :------ |
| `🟥_INVALID_VALUE` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you've sent a trade with an invalid value (your side and my side do not hold equal value).\n[You're missing: #value]" |
| `🟨_INVALID_ITEMS` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you've sent a trade with an invalid items (not exist in my pricelist)." |
| `🟧_DISABLED_ITEMS` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because the item(s) you're trying to take/give is currently disabled." |
| `🟦_OVERSTOCKED` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're attempting to sell item(s) that I can't buy more of." |
| `🟩_UNDERSTOCKED` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're attempting to purchase item(s) that I can't sell more of." |
| `🟫_DUPED_ITEMS` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because I don't accept duped items." |

## - Declined with other reasons [^](#table-of-content)

| Reason | Default |
| :--: | :------ |
| `general` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined" |
| `hasNonTF2Items` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because the offer you've sent contains Non-TF2 items." |
| `giftNoNote` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because the offer you've sent is an empty offer on my side without any offer message. If you wish to give it as a gift, please include "gift" in the offer message. Thank you." |
| `giftFailedCheckBanned` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because the offer you've sent is a gift, but I've failed to check your reputation status." |
| `crimeAttempt` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're taking free items. No." |
| `onlyMetal` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you might forgot to add items into the trade." |
| `duelingNot5Uses` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because your offer contains Dueling Mini-Game(s) that does not have 5 uses." |
| `noiseMakerNot25Uses` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because your offer contains Noise Maker(s) that does not have 25 uses" |
| `highValueItemsNotSelling` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're attempting to purchase %highValueName%, but I am not selling it right now." |
| `notTradingKeys` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because I am no longer trading keys. You can confirm this by typing "!price Mann Co. Supply Crate Key" or "!autokeys"." |
| `notSellingKeys` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because I am no longer selling keys. You can confirm this by typing "!price Mann Co. Supply Crate Key" or "!autokeys"." |
| `notBuyingKeys` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because I am no longer buying keys. You can confirm this by typing "!price Mann Co. Supply Crate Key" or "!autokeys"." |
| `banned` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're currently banned on backpack.tf or labeled as a scammer on steamrep.com or another community." |
| `escrow` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because I do not accept escrow (trade holds). To prevent this from happening in the future, please enable Steam Guard Mobile Authenticator.\nRead:\n• Steam Guard Mobile Authenticator - https://support.steampowered.com/kb_article.php?ref=8625-WRAH-9030\n• How to set up Steam Guard Mobile Authenticator - https://support.steampowered.com/kb_article.php?ref=4440-RTUI-9218" |
| `manual` | "/pre ❌ Ohh nooooes! The offer is no longer available. . Reason: The offer has been declined by the owner." |
| `failedToCounter` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined. Counteroffer is not possible because either one of us does not have enough pure, or Steam might be down, or your inventory is private (failed to load your inventory)." |
| `takingItemsWithZeroSellingPrice` | "/pre ❌ Ohh nooooes! The offer is no longer available. Reason: The offer has been declined because you're attempting to take/buy items without selling price" |

## - Accepted message [^](#table-of-content)

### • Automatic [^](#table-of-content)
| Type | Default |
| :--: | :------ |
| `bigOffer` | I have accepted your offer. The trade may take a while to finalize due to it being a large offer. If the trade does not finalize after 5-10 minutes has passed, please send your offer again, or add me and use the !sell/!sellcart or !buy/!buycart command. |
| `smallOffer` | I have accepted your offer. The trade should be finalized shortly. If the trade does not finalize after 1-2 minutes has passed, please send your offer again, or add me and use the !sell/!sellcart or !buy/!buycart command. |

### • Manual [^](#table-of-content)
| Type | Default |
| :--: | :------ |
| `bigOffer` | .\nMy owner has manually accepted your offer. The trade may take a while to finalize due to it being a large offer. If the trade does not finalize after 5-10 minutes has passed, please send your offer again, or add me and use the !sell/!sellcart or !buy/!buycart command. |
| `smallOffer` | .\nMy owner has manually accepted your offer. The trade should be finalized shortly. If the trade does not finalize after 1-2 minutes has passed, please send your offer again, or add me and use the !sell/!sellcart or !buy/!buycart command. |


# Gift keywords [^](#table-of-content)

```js
[
    'gift',
    'donat',        // So that 'donate' or 'donation' will also be accepted
    'tip',          // All others are synonyms
    'tribute',
    'souvenir',
    'favor',
    'giveaway',
    'bonus',
    'grant',
    'bounty',
    'present',
    'contribution',
    'award',
    'nice',         // Up until here actually
    'happy',        // All below people might also use
    'thank',
    'goo',          // For 'good', 'goodie' or anything else
    'awesome',
    'rep',
    'joy',
    'cute'
]
```

# Forced review keywords [^](#table-of-content)
```js
[
    'refund',
    'review',
    'check',
    'manual'
]
```
