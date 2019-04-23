---
title: 「PS4」The Surge SW Editing
top_img: https://b1.gmbox.ru/c/135291.jpg
tags: [PS4, SaveWizard]
categories: [Game Hack]
---

>Lovely! PS Plus finally give away The Surge! This is a DarkSoul-like RPG, with amazing roadmap and boss fight design.
![](https://hdqwalls.com/download/the-surge-game-5k-sd-2560x1440.jpg)
<!-- more -->

## Weapon proficiency & Core level
Weapon proficiency use 6 digits float point.  
For example, level `31.117435` in terms of hex is `0x41f8f082`. And this hex is exactly what you need to put into the editor in the advance mode.  Due to the crazy high damage in high weapon proficiency, most enemies will get one-shoted. So if you want to farm some gears, make sure the proficiency is at most Lv.30.

The following are the memory address for weapon proficiency:
```
0x000005CD 461C3C00 (One-handed: 9999 weapon proficiency)
0x000005D1 461C3C00 (Staff: 9999 weapon proficiency)
0x000005D5 461C3C00 (Heavy-Duty: 9999 weapon proficiency)
0x000005D9 461C3C00 (Single-Rigged: 9999 weapon proficiency)
0x000005DD 461C3C00 (Twin-Rigged: 9999 weapon proficiency)
```

At last, some quick codes:
```
All weapon proficiency Max
200005CC 3C1C4600
200005D0 3C1C4600
200005D4 3C1C4600
200005D8 3C1C4600
200005DC 3C1C4600
200005E0 00803F00

Core Level Max
10000552 0000270F
```

## Item Modding
Here is the structured piece of memory for one item, every slot is quoted with a <>:
```
00<18 12 a3 bb>00 00 00 00 00 00 00 00 00 00 00
<01>00 00 <00 01>3f 80 00 00 00 00 00<00>00 00 00
<00>00 00 00 00 00 00 00<01 20 e4 bf 0a>00 00 00
00 00 00 00 00 00 00 00<00>00 00 00 00 00 00 00

Slot 1: Item ID
Slot 2: Gear level (Gear/Weapon MAX is 0A in NG+)
Slot 3: Item quantity (For crafting materials)
Slot 4: Equip status (None-00, Right Side-08, Left Side-18, Weapon-28)
Slot 5: Implants slot
Slot 6: Gear type (Implants  is 0120E4BF0A, Gear is 017F3E9B99)
Slot 7: Injector shots quantity (No actual effect when modify)
```
You can simply change the item ID to replace items you don't want. So far as I discovered, most upgraded versions of implants have `+X` of the memory value base on their original implant MK level.  
But weapons and some implants (mostly from DLC) don't follow this pattern.
```
Ex: 
Voltaic Dynamo v.1 ---- AE1223B2
Voltaic Dynamo v.2 ---- AE1223B3 (+1)
or
Vital Boost v.1 ---- 1812A3BB
Vital Boost v.3 ---- 1812A3BD (+2)
Vital Boost v.5 ---- 1812A3BF (+2)
```

## Some of the useful item IDs
Please visit the document:
[点击这里](http://note.youdao.com/noteshare?id=6f2066a6387f84474be1ca9d22a4342d)  
[HERE](https://www.evernote.com/shard/s339/sh/d73e2e72-6b66-4bce-8441-7d015677fb05/7ec1d29e7498b95f6e98bc09317945c7)