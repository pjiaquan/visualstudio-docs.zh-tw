---
title: "索引標籤、所有語言、文字編輯器、選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs"
helpviewer_keywords: 
  - "縮排, 程式碼編輯器"
  - "程式碼編輯器, 預設行為"
  - "索引標籤, [程式碼編輯器] 中的設定"
  - "所有語言文字編輯器選項對話方塊"
  - "編輯器, 程式碼編輯器"
  - "程式碼編輯器, 縮排"
  - "程式碼編輯器, 索引標籤"
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 索引標籤、所有語言、文字編輯器、選項
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個對話方塊可讓您變更程式碼編輯器的預設行為。  這些設定也會套用到其他以程式碼編輯器為基礎的編輯器，例如 HTML 設計工具的來源檢視。  如果要顯示這些選項，請從 \[**工具**\] 功能表中選取 \[**選項**\]。  在 \[**文字編輯器**\] 資料夾中展開 \[**所有語言**\] 子資料夾，然後選擇 \[**定位點**\]。  
  
> [!CAUTION]
>  這個頁面可以設定所有開發語言的預設選項。  請記住，如果在這個對話方塊中重設選項，則所有語言的 \[定位點\] 選項都會重設成此處所選的選項。  如果只想變更一種語言的文字編輯器選項，請展開該語言的子資料夾，並選取其選項頁面。  
  
 如果在 \[定位點\] 選項頁面上根據特定的程式設計語言選取了不同的設定，則不同的 \[**縮排**\] 選項就會顯示「個別文字格式的縮排設定彼此衝突」訊息，不同的 \[**定位點**\] 選項則會顯示「個別文字格式的定位點設定彼此衝突」訊息。  例如，當 Visual Basic 選擇 \[**智慧型縮排**\] 選項，但是 Visual C\+\+ 選擇 \[**縮排區塊**\] 時，就會出現提醒訊息。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 縮排  
 None  
 如果選取這個選項，新行不會縮排。  插入點會放在新行的第一欄中。  
  
 區塊  
 如果選取這個選項，新行會自動縮排。  插入點會放在與前一行相同的起始點。  
  
 智慧型  
 如果選取這個選項，便會依據程式碼內容、每個其他程式碼的格式設定，以及開發語言的 IntelliSense 慣例，調整新行的位置。  不過，並非所有的開發語言都有這個選項。  
  
 例如，左邊的大括號 \({\) 和右邊的大括號 \(}\) 之間的行，會自動從對齊的括號位置縮排一個定位停駐點 \(Tab Stop\)。  
  
## Tabs  
 定位點大小  
 設定定位停駐點 \(Tab Stop\) 之間的距離 \(以空格為單位\)。  預設值為四個空格。  
  
 縮排大小  
 設定自動縮排的大小 \(以空格為單位\)。  預設值為四個空格。  插入定位字元、空格字元或兩者，以填滿指定的大小。  
  
 插入空格  
 如果選取這個選項，縮排作業只會插入空格字元，而非定位字元。  例如，如果 \[**縮排大小**\] 設定為 5，每當您按下 TAB 鍵，或 \[**格式**\] 工具列的 \[**增加縮排**\] 按鈕，就會插入 5 個空格字元。  
  
 保留定位點  
 選取時，縮排作業會插入盡可能多的定位字元。  每個定位字元都會以指定的 \[**定位點大小**\] 填入空格數。  如果 \[**縮排大小**\] 不是 \[**定位點大小**\] 的偶數倍數，就會加入空格字元填滿其間的差距。  
  
## 請參閱  
 [選項，文字編輯器，所有語言](../../ide/reference/options-text-editor-all-languages.md)   
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)