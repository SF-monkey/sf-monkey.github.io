---
title: 「PS4」Resident Evil 2 Remake SW Quick Code
top_img: https://www.amd.com/system/files/2018-11/184189-re2-key-art-1920x800.jpg
tags: [PS4, SaveWizard]
categories: [Game Hack]
---

>Here's why Mr.X is much more invincible than it was: Now he's got a fedora!!
![](https://i.ytimg.com/vi/3PoWMBvvX9c/maxresdefault.jpg)
<!-- more -->

## Quick Code
Let's cut the bullshit.  

1. This cheat will **replace** the Matilda Handgun / SLS 60 Handgun with the Infinite Anti-Tank Rocket (4 rounds ver.)  
2. Use this on your Autosave file **as soon as you start the game and trigger auto saving**  
3. Works on all difficulties, both Leon and Claire  
4. Can get S+, as long as meeting the number of saves / total play time requirements.  


### Leon - AutoSave - ATM-4    
```
80020024 2D727526
F5C58BAA 01000000
04000000 00000000
9DB32976 01000000
04000000 01000000
08000020 000000F2
08000030 00000000
08000040 0000001C
08000050 00000004
```

### Claire - AutoSave - ATM-4
```
80020024 2D727526
F5C58BAA 01000000
04000000 00000000
9DB32976 01000000
04000000 09000000
08000020 000000F2
08000030 00000000
08000040 0000001C
08000050 00000004
```

### Infinite Health
```
80010008 D3A8A66D
633EECF7 00000000
28000010 7FFFFFFF
```

### Change Difficulty  
Replace 'xx' with:  
`00`: ASSISTED  
`01`: STANDARD  
`02`: HARDCORE
```
8001000C 8C26C0AA
01000000 04000000
2800000C 000000xx
```

## Advanced Items Modding

The following section is for items modding.  
**Before trying to edit anything, it is essential to backup your saves!!!**  

1. Load your game save (Auto Save or Manual Save), it is best that you edit your save **right after you encounter your first item box**. I will explain why down below.  
2. Search `00000053` for **Handgun - Samurai Edge (Chris Model)** since it is already in the box as a pre-order bouns. (If you don't have anything in the item box, then place an item in it, save, then search for its corresponding item ID.)  
3. You can see code chunks like this:  
```
2D 72 75 26 (START of 1ST INVENTORY SLOT in ITEM BOX)
00 00 00 00 (LINE for ITEMs ID, 00000000 MEANS IS WEAPON)
53 00 00 00 (LINE for WEAPONs ID, FFFFFFFF MEANS NOT WEAPON)
00 00 00 00 (LINE for WEAPONs CUSTOMs, 00000000 WHEN NOT WEAPON)
0F 00 00 00 (LINE for AMMO TYPE IN WEAPON, 00000000 WHEN NOT WEAPON)
00 00 00 00 (LINE for AMMO AMOUNTS, E7030000 IS 999.MAXIMUM)
2D 72 75 26 (START of 2ND INVENTORY SLOT in ITEM BOX)
```
4. Edit the above code chunk with what you need.
5. Full List of Item IDs: [点击这里](https://docs.qq.com/doc/DQnlqT1dtQ2FVZ1N6) or [HERE](https://docs.google.com/spreadsheets/d/1TUDs7BtM5AurD3oepdAfRXfRkmqa6hKpVPHL2SqfO58/edit?usp=sharing)

### PS: Avoid The Mess!
The reason I recommend editing the save in the very beginning of the game is that the addresses for item boxes vary by their locations. More item boxes you encounter, higher chance of multiple addresses when you search for a particular item.  
If you do need to edit the save after passing the story to a certain point, one possible approach is to put a fresh item, say a new type of ammo box, into the item box -- save -- extract the decrypted save -- change the item amount with the official SW quick codes -- extract the decrypted save -- compare hex.  
This would possibly help you locate the address for the new item box.  
Still, the best practice is to avoid this mess!