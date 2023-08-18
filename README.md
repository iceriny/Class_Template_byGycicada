# **Mod模版介绍**

### 这是一个用于职业模组的模板。应该能够帮助你开始制作任何你想要的职业模组。

****

#### **工具**
##### 确保你拥有必要的工具，特别是：
1. 由Norbyte开发的[LSLib](https://github.com/Norbyte/lslib "导出工具")。这可以让你对文件进行打包和解包，转换文件类型，并具有许多强大的功能。
   
2. [Modder's Multitool](https://github.com/ShinyHobo/BG3-Modders-Multitool "Moder的多重工具")。设置可能需要一些时间，请遵循其说明。该程序允许你搜索游戏文件，以查看是否有任何可以重新使用或复制的内容。

##### 你可能想要使用的其他一些工具：
1. [图标生成](https://www.nexusmods.com/baldursgate3/mods/521 "AI图标生成")：模型使用stable diffusion来生成给定提示的图标（保持简短）。
2. 图像编辑软件：我比较节省，所以不会购买Photoshop。[GIMP](https://www.gimp.org)已经提供了我需要的一切。
3. 某种不是基本记事本的文本编辑软件。我一直在使用[Notepad++](https://notepad-plus-plus.org)，我个人认为它相当不错。
4. Larian的官方Discord服务器。如果你有任何问题，那里有很多人乐意提供帮助。

##### 为文件结构所做的其他有用的事情：

1. 一个专门用于**制作**的工作区，其中包含所有的工具。
2. 工作区内的一个文件夹，专门用于所有**已提取的模组**或**正在进行的模组**。我发现查看其他人的模组很有用，以了解他们是如何实现某个功能以获取灵感，或者只是看看可能性。
3. 到**AppData\Local\Larian Studios\Baldur's Gate 3\Mods**的快捷方式。在尝试修复令人讨厌的错误时，你将经常在工作区、Mods文件夹之间切换。


##### **其他**
<details>
<summary>英语原文-点击展开：</summary>
This is a mod template for class mods. Should get you started in whatever class you want to make.

Make Sure you have the tools necessary, namely:

1. LSLib by Norbyte (Export Tool). this let you pak and unpak files, convert file types, and a lot of powerful functions 
	(https://github.com/Norbyte/lslib)
2. Modder's Multitool. this will take a bit to set up, follow its instructions. This program allows you to search through game files to see if there is anything that you might be able to reuse or copy. 
	(https://github.com/ShinyHobo/BG3-Modders-Multitool)

Some other tools that you might want to use

1. Icons Generation: A modle uses stable diffusion to generate Icons with given prompt (keep it short). (https://www.nexusmods.com/baldursgate3/mods/521)
2. Image editing Software: Im cheap so im not going to pay for photoshop. GIMP gives me everything i need anyways (https://www.gimp.org)
3. Some sort of text editing software that is not the base Notepad. I have been using Notepad++ and its pretty good imo (https://notepad-plus-plus.org)
4. Larian's Official Discord Server. If you have any questions, a lot of people there are happy to help.

Some useful things I do for organization

1. a workspace decicated to modding with all of the tools in there
2. a folder inside the workspace dedicated to all extracted mods or WIP mods. I find it useful to take a look at other's mods to see how they might have implemented a feature to get inspiration, or just to see whats possible.
3. a shortcut to AppData\Local\Larian Studios\Baldur's Gate 3\Mods. You will be navigating between those your Workspace and the Mods folder very frequently espeically when trying to fix an annoying bug.
</details>

****

#### **文件夹结构**

*这个结构不包括脚本或模组修复工具*

* **Mod Folder** =>Mod文件夹
	* **Localization** =>本地化文件夹
		* Language =>语言文件夹(例如"Chinese")
			* *.loca =>游戏可以读取的文件
			* *.xml =>编辑文件
	* **Mods**
		* *一个以你的模组(**职业**)名称命名的文件夹（大小写要匹配）*
		    * meta.ls =>Mod元数据
	* **Public**
		* *一个以你的模组(**职业**)名称命名的文件夹（大小写要匹配）*
			* ActionResourceDefinitions =>动作资源定义
				* `ActionResourceDefinitions.lsx` =>如果你的*职业*使用了独特的资源，那么你就在这里创建它
			* Assets =>资产
				* Textures
					* Icons
						* `*.DDS` =>你的图标集合
			* CharacterCreationPresets =>角色创建预设
				* `AbilityDistributionPresets.lsx` =>技能分布预设；非必要
			* ClassDescriptions =>职业说明
				* `ClassDescriptions.lsx` =>在这里你将定义你的职业，并使其在角色创建中显示，尽管仅有这个文件在角色创建中选择时会导致游戏崩溃。
			* Content
				* UI
					* [PAK]_UI
						* `_merged.lsx` => 用于编辑
						* `_merged.lsf` => 从Assets\Textures\Icons\Example.DDS加载.  加载DDS文件到游戏中。
			* GUI
				* `Icons_Example.lsx` => 这个文件将加载的.DDS文件切割成块，这样你可以将更多的图标放入同一张图纸中。
			* Lists
				* `PassiveLists.lsx` => 可能适用于你的职业的被动技能列表（类似于术士的召唤术或魔法师的奥秘 (like Warlock's invocations, or Magus' Arcanas)）。
				* `SkillLists.lsx` => 角色创建时可以选择的技能列表，或者在其他时候也可以选择，比如如果你的职业拥有专长等。
				* `SpellLists.lsx` => 各种法术列表，不仅仅限于魔法法术，像武器攻击这样的东西在BG3中也被视为“法术”。
			* Progressions
				* `Progressions.lsx` => 在这里定义你的职业的具体等级以及他们会获得什么。要让一个职业正常工作，你最少需要这个文件和ClassDescriptions.lsx文件。
			* Stats
				* Generated
					* Data (这个文件夹内的文件名并不重要。)
						* `Interrupt.txt` => 任何你希望涉及弹出窗口的内容（主要是反应）
						* `Passive.txt` =>  用于定义被动技能
						* `Spell.txt` => 用于定义法术
						* `Status_BOOSTS.txt` => 用于定义状态增益效果
					* `Equipment.txt` =>  起始装备
