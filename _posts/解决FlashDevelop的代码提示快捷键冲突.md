title: "解决FlashDevelop的代码提示快捷键冲突"
date: 2015-04-02
tags: 
- AS3
- FlashDevelop
categories:
- AS3
---

FlashDevelop代码提示快捷键为Ctrl+Space。和中文系统的语言切换快捷键冲突。

解决方案：

1.D:\Program Files (x86)\FlashDevelop\Settings\MainMenu.xml复制到

C:\Users\Rain\AppData\Local\FlashDevelop\Settings

2.打开MainMenu.xml

3.在你喜欢的地方加上：

	<button label="Control Space" click="PluginCommand" tag="ASCompletion.CtrlSpace" shortcut="Alt|C" flags="Enable:IsEditable" />

	<button label="Control Shift Space" click="PluginCommand" tag="ASCompletion.CtrlShiftSpace" shortcut="Alt|Shift|C" flags="Enable:IsEditable" />

	<button label="Control Alt Space" click="PluginCommand" tag="ASCompletion.CtrlAltSpace" shortcut="Control|Alt|C" flags="Enable:IsEditable" />