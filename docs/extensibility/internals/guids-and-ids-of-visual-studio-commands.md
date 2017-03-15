---
title: "Guid 和 Id 的 Visual Studio 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令"
  - "id"
  - "命令位置"
  - "visual studio 命令"
  - "guid"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Guid 和 Id 的 Visual Studio 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

已安裝做為 Visual Studio 的 SDK 的一部分的.vsct 檔案中定義的 GUID 及識別碼的值包含在 Visual Studio 的整合式的開發環境 \(IDE\) 中的指令。  如需詳細資訊，請參閱 [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 如需有關如何使用.vsct 檔案中定義的 IDE 物件的詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## 尋找命令定義  
 由於 Visual Studio 會定義超過一千命令，不適合這裡將它們列出。  相反地，請依照下列步驟找出的命令定義。  
  
#### 找不到命令定義  
  
1.  在 Visual Studio 中，開啟下列檔案中的 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Common\\Inc\\ 資料夾： SharedCmdDef.vsct、 ShellCmdDef.vsct、 VsDbgCmdUsed.vsct、 Venusmenu.vsct。  
  
     大部份的 Visual Studio 指令被定義在 SharedCmdDef.vsct 和 ShellCmdDef.vsct。  VsDbgCmdUsed.vsct 定義適用於偵錯工具的命令，Venusmenu.vsct 定義是針對 Web 程式開發的命令。  
  
2.  如果指令的功能表項目，請注意，功能表項目完整文字。  如果指令的工具列上的按鈕，請注意當您在上面時，就會出現工具提示文字。  
  
3.  按 CTRL \+ F 開啟**到**對話方塊。  
  
4.  在**尋找**方塊中，在步驟 2 中輸入您記下的文字。  
  
5.  確認**所有開啟的文件** 會顯示在 **查詢**方塊。  
  
6.  按一下 \[ **尋找下一個**按鈕中選取的文字，直到`<Strings>`一節的[Button 元素](../../extensibility/button-element.md)。  
  
     `<Button>`指令是出現在中的項目是命令定義。  
  
 當你已經找到命令定義時，您可以藉由建立另一個功能表或工具列上讓一份命令[CommandPlacement 項目](../../extensibility/commandplacement-element.md) ，具有相同`guid`和`id`和命令的值。  如需詳細資訊，請參閱 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
### 特殊案例  
 在下列情況中，功能表文字 」 或 「 工具提示文字可能不完全相同的命令定義。  
  
-   功能表項目，包括未加上底線的字元，例如**列印** 命令 **檔案** \] 功能表中，p 加底線。  
  
     顯示前面會加上 '&' 字元功能表項目名稱中的字元加底線。  不過，.vsct 檔案以 XML，這會使用 '&' 字元來表示特殊字元，而且需要顯示一個連字號必須拼，做為 ' & amp;'。  因此，在.vsct 檔案中，  **p**rint 命令會顯示為 ' & amp;列印 '。  
  
-   命令有動態文字，例如， **儲存***目前的檔名*，並動態產生的功能表項目，例如項目上 **最近使用的檔案**清單。  
  
     搜尋動態文字沒有可靠的方式。  相反地，尋找您想要的命令裝載 \(host\) 可藉由參考群組[Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)，並搜尋該群組的識別碼。  如果命令定義就不需要為群組其[Parent 項目](../../extensibility/parent-element.md)，搜尋 SharedCmdPlace.vsct 和 ShellCmdPlace.vsct \(或偵錯工具命令的 VsDbgCmdPlace.vsct\) `<CommandPlacement>`設定命令的父代的項目。  SharedCmdPlace.vsct，ShellCmdPlace.vsct，andVsDbgCmdPlace.vsct 是在 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Common\\Inc\\ 資料夾。  
  
## 請參閱  
 [MenuCommand 對比 OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)