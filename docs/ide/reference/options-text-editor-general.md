---
title: "一般、文字編輯器、選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "文字編輯器選項對話方塊"
  - "程式碼編輯器"
  - "文字編輯器 [Visual Studio]"
  - "編輯器, 全域設定"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 一般、文字編輯器、選項
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個對話方塊可讓您變更 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 程式碼和文字編輯器的全域設定。  若要顯示這個對話方塊，請按一下 \[**工具**\] 功能表上的 \[**選項**\]，展開 \[**文字編輯器**\] 資料夾，然後按一下 \[**一般**\]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 設定  
 拖放文字編輯  
 如果選取這個選項，當您利用滑鼠選取文字並加以拖曳後，便可以將文字移動至目前文件中的其他位置，或移動至任何其他開啟的文件。  
  
 分隔符號自動反白顯示  
 如果選取這個選項，分隔參數或項目\/值組的分隔字元以及對稱的大括號就會以反白顯示。  
  
 追蹤修訂  
 在程式碼編輯器時，一條黃色線在選取範圍框線外觀指示已變更的程式碼，因為檔案最近已儲存。  當您儲存變更時，垂直線變成綠色。  
  
 自動偵測無簽章 UTF\-8 編碼  
 編輯器預設的編碼偵測方式，是搜尋位元組順序標記或 charset 標記。  如果目前文件中找不到這兩種標記，程式碼編輯器就會試著掃描位元組序列，自動偵測 UTF\-8 編碼。  若要停用自動偵測編碼，請清除這個選項。  
  
## Display  
 選取範圍邊界  
 如果選取這個選項，編輯器文字區域左緣會顯示一條垂直邊界。  按一下這個邊界即可選取整行文字，按一下邊界後拖曳則可選取連續數行的文字。  
  
|開啟選取範圍邊界|關閉選取範圍邊界|  
|--------------|--------------|  
|![HTMLpageSelectionMarginOn 螢幕擷取畫面](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![HTMLpageSelectionMarginOff 螢幕擷取畫面](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 指示區邊界  
 如果選取這個選項，編輯器文字區域左緣外側會顯示一條垂直邊界。  按一下邊界，與文字相關的圖示和工具提示隨即出現。  例如，中斷點或工作清單捷徑會出現在指示區邊界內。  指示區邊界資訊無法列印。  
  
 垂直捲軸  
 如果選取這個選項，就會顯示垂直捲軸，讓您上下捲動來檢視位於編輯器檢視區域外的項目。  如果無法使用垂直捲軸，可使用 Page Up、Page Down 和游標鍵來捲動。  
  
 水平捲軸  
 如果選取這個選項，會顯示水平捲軸，這個水平捲軸可讓您從兩邊捲動來檢視位於編輯器檢視區域外的項目。  如果無法使用水平捲軸，可使用游標鍵來捲動。  
  
 反白顯示目前這一行  
 選取此選項時，會出現一個灰色方塊在游標的程式碼周圍。  
  
## 請參閱  
 [選項，文字編輯器，所有語言](../../ide/reference/options-text-editor-all-languages.md)   
 [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [副檔名、文字編輯器、選項](../../ide/reference/options-text-editor-file-extension.md)   
 [識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [自訂編輯器](../../ide/customizing-the-editor.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)