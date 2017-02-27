---
title: "格式、C#、文字編輯器、選項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "格式化 [C#]"
  - "格式化 [J#]"
  - "[文字編輯器選項] 對話方塊, 格式化"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 格式、C#、文字編輯器、選項
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 \[**格式化**\] 屬性頁 \(Property Page\) 對話方塊設定在程式碼編輯器 \(Code Editor\) 中格式化程式碼的選項。  若要存取這個對話方塊，請按一下 \[**工具**\] 功能表上的 \[**選項**\]，展開 \[**文字編輯器**\]、\[**C\#**\]，然後按一下 \[**格式**\]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 一般設定  
 一般設定會影響程式碼編輯器套用格式化選項至程式碼的方式。  
  
## UIElement 清單  
  
|Label|描述|  
|-----------|--------|  
|**於 ; 完成陳述式自動格式化**|若選取這個方塊，則會在完成陳述式時，根據為程式碼編輯器所選取的格式化選項格式化陳述式。  如果您不要程式碼編輯器修改陳述式，則清除這個方塊。|  
|**於 } 完成程式碼區塊自動格式化**|若選取這個方塊，會在完成程式碼區塊 \(Code Block\) 時，根據針對程式碼編輯器選取的格式化選項格式化程式碼區塊。  如果您不要程式碼編輯器修改區塊，則清除這個方塊。|  
|**貼上時調整縮排**|若選取這個方塊，則會依據針對程式碼編輯器選取的格式化選項，格式化貼入程式碼編輯器的文字。  如果您不要修改貼上的文字，則清除這個方塊。|  
  
## 預覽視窗  
 \[**縮排**\]、\[**新行**\]、\[**間距**\] 及 \[**換行**\] 選項的窗格都會顯示預覽視窗。  預覽視窗會顯示各選項的效果。  若要使用預覽視窗，請選取格式化選項。  預覽視窗會顯示所選取選項的範例。  當您變更設定時 \(例如選取或清除核取方塊\)，便會更新預覽視窗，並顯示新設定的效果。  
  
## 備註  
 每種語言的 \[**索引標籤**\] 頁面上的 \[縮排\] 選項只會決定，當您在行尾按下 ENTER 鍵時，程式碼編輯器放置游標的位置。  自動格式化程式碼時 \(例如，當您在已選取 \[**貼上時調整縮排**\] 的情況下將程式碼貼入檔案時，或手動輸入要格式化的區塊時\)，則會套用 \[**格式化**\] 下的 \[縮排\] 選項。  
  
## 請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)