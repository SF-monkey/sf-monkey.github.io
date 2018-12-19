---
title: 「PS4港中Ver」噬神者2狂怒解放 SW修改教程
top_img: http://steam.cryotank.net/wp-content/gallery/godeater2/God-Eater-2-02-HD-textless.png
---

关于噬神者2RB，日版修改器能够修改的选项很多，反观SW只有两条，而且经过测试修改还无效。。。。  
所以自己研究了下存档，提供一些心得给大家。当然还有很多修改选项我也不会弄，所以本教程算是抛砖引玉吧，欢迎大神们来讨论指点！  

前言：  
港中版跟欧美版和日版在存档上有些不同，具体是部分数据和编码字符集有变化。  
欧美版由于是英文，存档编码为ANSI，在SW上可以直接辨认道具的名称。  
而港中或日版由于有汉字，编码需要改成了Unicode UTF-8才能正常显示。  
知道这点后，由于SW没有自带多种字符集，所以只能高级模式提取存档出来后再用Hex编辑器搞了，这里我用的是WinHex。  

***

### <font color="Blue" size="5">简易代码 | Quick Codes</font>  
 <font color="Blue" size="5"><b>(HK ver ONLY as offsets are different across regions)</b></font>

Max Money  
```
42005B38 3B9AC9FF  
40010000 00000000  
```
Max GAP  
```
10016930 000003E7  
```

All Charater Max AP  
```
42072060 0001869F  
40800128 00000000  
```

Max Storage Item (2000 Slots)  
```
41016944 000003E7  
47D00020 00000000  
```

Max Battle Record  
```
410541DE 0000270F  
400A0002 00000000  
410542BC 0000270F  
40040004 00000000  
```

Max Blood Arts ([Click for tutorial](http://www.nextgenupdate.com/forums/ps4-game-save-modding/952136-god-eater-2-rage-burst-save-editor-4.html#post7358626))  
```
4007B478 00000006  
41C30004 00000000  
```
***

### <font color="Blue" size="5">武器技能修改 | Weapon Skills Modding</font>  

先上图，这里以黑钢重火型这把武器作为修改范例。  
![](http://file1.a9vg.com/data/attachment/forum/201805/02/1053293hwfps9qf0dhfhhs.png)

1\. 每个武器装备都有自己的物品ID，找这些ID的方法有俩：先装备上，然后在第一个地址位置（1000+）找ID；或者对照装备的技能列表确定你选取的装备的ID。这里我推荐第一种，比较直观。  

2\. 每个物品ID格式为<font style="background-color:Yellow">XX XX XX XX</font>， 具体位置是从武器中文名字前面的一排FF那里开始倒数第16个位置开始。如图中，从第一个FF那里往前数16位，就得到<font style="background-color:Yellow">AC 16 0F 02</font>这个ID，这个ID对应的装备是黑钢重火型。  

3\. 每个装备ID会储存在存档里3个位置，第一个位置（地址1000+）是目前玩家装备上的武器道具，第二个（地址20000+）是玩家仓库里的武器道具，第三个（50000+）位置未知。我们要修改的是第二个位置的装备数据，因为这样可以永久保存修改效果。  

![](http://file1.a9vg.com/data/attachment/forum/201805/02/110721z3hjdwewyxzzi4xz.png)

4\. 从上图我们已经来到了第二个黑钢重火型的数据储存地址，可以看到<font style="background-color:Yellow">AC 16 0F 02</font>再次出现。我们往后数8个位，蓝色的那4组<font style="background-color:Silver">AA AA 0A 00</font>数据就是武器所携带的技能，它的格式为：  
**AA AA** 为技能ID（感谢楼下坛友 **<font color="Blue">shimotsuki</font>** 提供部分中文技能ID列表）；  
**<font color="#ff0000">较为完整的技能ID在这，用法是将10进制技能ID转换成16进制即可：</font>**  
[All ID skill name of GOD EATER 2 Rage Burst](https://fearlessrevolution.com/threads/all-id-skill-name-of-god-eater-2-rage-burst.2463/)  
**0A** 为技能等级，最高10级，所以填0A；   
**00(美版为EF)** 为分隔符，填00即可不用管；  
蓝色的技能后面的1E，是这把武器的附加等级，最高+30，所以填1E。  

整套代码下来成品是这样（4技能，武器等级+30）：  
![](http://file1.a9vg.com/data/attachment/forum/201805/02/11203618zurnrajpq1lrnt.jpg)

这里提供一下我目前在用的装备的代码：  

近战武器 [劍聖+專家+神諭細胞管控者+猛攻]：  
 <font color="Red">A6 02 0A 00</font> <font color="SandyBrown">9B 02 0A 00</font> <font color="YellowGreen">A9 02 0A 00</font> <font color="MediumTurquoise">F9 00 0A 00</font> <font color="Gray">1E</font>  

射击枪身 [砲擊手+槍手接觸+機警射手+冷酷槍手]：
 <font color="Red">A2 02 0A 00</font> <font color="SandyBrown">8E 01 0A 00</font> <font color="YellowGreen">0E 01 0A 00</font> <font color="MediumTurquoise">D3 00 0A 00</font> <font color="Gray">1E</font>  

装甲盾牌 [風林火山+獾+不滅靈魂+登峰造極]：  
 <font color="Red">A1 02 0A 00</font> <font color="SandyBrown">AB 02 0A 00</font> <font color="YellowGreen">9A 00 0A 00</font> <font color="MediumTurquoise">9E 02 0A 00</font> <font color="Gray">1E</font>  

控制单元 (開荒) [血魂+七重天+束缚+猛毒]：  
 <font color="Red">9B 01 0A 00</font> <font color="SandyBrown">90 00 0A 00</font> <font color="YellowGreen">3F 00 0A 00</font> <font color="MediumTurquoise">45 00 0A 00</font> <font color="Gray">1E</font>  

控制单元 (后期) [芽孢桿菌+輔助+威猛+束缚]：  
 <font color="Red">9E 00 0A 00</font> <font color="SandyBrown">9C 02 0A 00</font> <font color="YellowGreen">C8 01 0A 00</font> <font color="MediumTurquoise">3F 00 0A 00</font> <font color="Gray">1E</font>  

强化零件1 [反射+亂世英雄+大蛇怒號+野性之手]：  
 <font color="Red">54 01 0A 00</font> <font color="SandyBrown">A0 02 0A 00</font> <font color="YellowGreen">A3 02 0A 00</font> <font color="MediumTurquoise">A5 02 0A 00</font> <font color="Gray">1E</font>  

强化零件2 [面面俱到+健康管控者+肉體管控者+鋼鐵身體]：  
 <font color="Red">86 00 0A 00</font> <font color="SandyBrown">A8 02 0A 00</font> <font color="YellowGreen">A7 02 0A 00</font> <font color="MediumTurquoise">9D 02 0A 00</font> <font color="Gray">1E</font>  

***

### <font color="Blue" size="5">A-F票，素材修改 | Tickets, Items Modding</font>  

![](http://file1.a9vg.com/data/attachment/forum/201805/11/1623040pj5q0m0zqbcrblp.png)

如图，地址段[000000EE-00000EFA]是你目前持有的物品，大概有30个物品位。  
跟装备一样，每个道具也有一个ID。我们要做的就是把持有物品换成想要物品的ID，再把数量改满。  
在每个物品名字的前面会有刚好16组FF，再往前面12位就是物品的ID，格式为 <font style="background-color:Yellow">XX XX XX XX</font> <font style="background-color:Silver">AA AA</font>。  
其中<font style="background-color:Yellow">XX XX XX XX</font>是ID，<font style="background-color:Silver">AA AA</font>是数量。如图中F票白金的ID为<font style="background-color:yellow">6D 27 0A 00</font>，数量为<font style="background-color:Silver">01 00</font>。  
理论上，只要你找到你想要物品的ID，然后把ID替换上去即可，物品的名字不需要修改，游戏载入时会自动纠正的。

这里提供下全部A-F票的ID：  
A铜：C0 1A 0A 00  
A银：C1 1A 0A 00  
A金：C2 1A 0A 00  
A白金：C3 1A 0A 00  
A黑：69 27 0A 00  
A钻石：27 26 0A 00

F铜：BD 1A 0A 00  
F银：BE 1A 0A 00  
F金：BF 1A 0A 00  
F白金：6D 27 0A 00  
F黑：6E 27 0A 00  
F钻石：6F 27 0A 00  

***

### <font color="Blue" size="5">服装修改 | Costumes Modding</font>  

因为99级挑战类的服装比较难获取，所以研究了下服装修改。  
服装修改跟道具物品修改类似，但稍微繁琐一些。  
我们依然是利用替换法，将一些已有的服装通过修改替换服装ID来获取新服装。  
![](http://file1.a9vg.com/data/attachment/forum/201805/18/183929an7x6uca8ungzuua.png)

如图，**<font size="4" color="Red">决定一件服装需要3个参数，缺一不可：服装名称，服装ID ①和服装ID ②</font>**；不过我们也能改数量。  

如何获取服装的参数？  
先正常存档一份，用SW高级提取解密存档，然后进入游戏删掉一件服装，再存档，再用SW高级提取解密存档。  
![](http://file1.a9vg.com/data/attachment/forum/201805/18/19023526zwiityh2z4twkz.png)

两份存档了而唯一的改动就是后者少了一件服装，现在需要用软件[HexCmp](http://www.fairdell.com/hexcmp/)对两个文件进行对比。发现有图中类似结构的地方有所改动，那基本可以确认刚才删掉的服装的一系列信息了。  
如上图作者删掉了3件衣服，那么标红色的改动就有3处，而且服装名称全部变成未知的FFFF，数量变0，其他不变。  

这里提供下全部等级挑战服装的<font color="#ff0000">**名称**</font>，<font color="#0000ff">**ID ①**</font>和<font color="#2e8b57">**ID ②**</font>：  

虎05：<font color="#ff0000">**C6 1F 0C 00**</font>, <font color="#0000ff">**30 12**</font>, <font color="#2e8b57">**16 01**</font>  
虎10：<font color="#ff0000">**C7 1F 0C 00**</font>, <font color="#0000ff">**31 12**</font>, <font color="#2e8b57">**17 01**</font>  
虎30：<font color="#ff0000">**C8 1F 0C 00**</font>, <font color="#0000ff">**32 12**</font>, <font color="#2e8b57">**18 01**</font>  
虎99：<font color="#ff0000">**C9 1F 0C 00**</font>, <font color="#0000ff">**33 12**</font>, <font color="#2e8b57">**19 01**</font>  

狼05：<font color="#ff0000">**CA 1F 0C 00**</font>, <font color="#0000ff">**34 12**</font>, <font color="#2e8b57">**1A 01**</font>  
狼10：<font color="#ff0000">**CB 1F 0C 00**</font>, <font color="#0000ff">**35 12**</font>, <font color="#2e8b57">**1B 01**</font>  
狼30：<font color="#ff0000">**CC 1F 0C 00**</font>, <font color="#0000ff">**36 12**</font>, <font color="#2e8b57">**1C 01**</font>  
狼99：<font color="#ff0000">**CD 1F 0C 00**</font>, <font color="#0000ff">**37 12**</font>, <font color="#2e8b57">**1D 01**</font>  

兵05：<font color="#ff0000">**CE 1F 0C 00**</font>, <font color="#0000ff">**38 12**</font>, <font color="#2e8b57">**1E 01**</font>  
兵10：<font color="#ff0000">**CF 1F 0C 00**</font>, <font color="#0000ff">**39 12**</font>, <font color="#2e8b57">**1F 01**</font>  
兵30：<font color="#ff0000">**D0 1F 0C 00**</font>, <font color="#0000ff">**3A 12**</font>, <font color="#2e8b57">**20 01**</font>  
兵99：<font color="#ff0000">**D1 1F 0C 00**</font>, <font color="#0000ff">**3B 12**</font>, <font color="#2e8b57">**21 01**</font>  

帝05：<font color="#ff0000">**D2 1F 0C 00**</font>, <font color="#0000ff">**3C 12**</font>, <font color="#2e8b57">**22 01**</font>  
帝10：<font color="#ff0000">**D3 1F 0C 00**</font>, <font color="#0000ff">**3D 12**</font>, <font color="#2e8b57">**23 01**</font>  
帝30：<font color="#ff0000">**D4 1F 0C 00**</font>, <font color="#0000ff">**3E 12**</font>, <font color="#2e8b57">**24 01**</font>  
帝99：<font color="#ff0000">**D5 1F 0C 00**</font>, <font color="#0000ff">**3F 12**</font>, <font color="#2e8b57">**25 01**</font>  

狐05：<font color="#ff0000">**D6 1F 0C 00**</font>, <font color="#0000ff">**40 12**</font>, <font color="#2e8b57">**26 01**</font>  
狐10：<font color="#ff0000">**D7 1F 0C 00**</font>, <font color="#0000ff">**41 12**</font>, <font color="#2e8b57">**27 01**</font>  
狐30：<font color="#ff0000">**D8 1F 0C 00**</font>, <font color="#0000ff">**42 12**</font>, <font color="#2e8b57">**28 01**</font>  
狐99：<font color="#ff0000">**D9 1F 0C 00**</font>, <font color="#0000ff">**43 12**</font>, <font color="#2e8b57">**29 01**</font>  

细心的朋友说不定已经发现了，无论服装的名称还是ID都是递进的^^  

***

教程先到这，然后据说武器的固有攻击力等数据不能修改，魔改子弹好像官方也禁了，所以没法改。。。  
欢迎大神来指导讨论补充！！