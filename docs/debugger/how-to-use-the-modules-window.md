---
title: "如何：使用模組視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.modules"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, [模組] 視窗"
  - "模組視窗"
  - "可執行檔, 偵錯時顯示"
  - "偵錯 [Visual Studio], 顯示模組"
  - "DLL, 偵錯時顯示"
  - "模組, 顯示"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用模組視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  這個功能不能用於 SQL 或指令碼偵錯。  
  
 \[**模組**\] 視窗會列出程式所使用的 DLL 和 EXE，並顯示每個項目的相關資訊。  
  
### 若要在中斷模式或執行模式顯示模組視窗  
  
-   在 \[**偵錯**\] 功能表上選擇 \[**Windows**\]，然後按一下 \[**模組**\]。  
  
     根據預設，\[**模組**\] 視窗會依載入順序將模組排序。  但您也可以選擇依任何資料行來排序。  
  
### 若要依任何欄位排序  
  
-   請按一下欄位頂端的按鈕。  
  
     您可以使用捷徑功能表，從 \[**模組**\] 視窗載入符號或指定符號路徑。  
  
## 載入符號  
 在 \[**模組**\] 視窗中，您可以查看哪些模組已載入偵錯符號。  這項資訊顯示在 \[**符號狀態**\] 欄位中。  如果這個狀態顯示為 \[**已略過載入**\]、\[**找不到或無法開啟 PDB 檔案**\] 或 \[**已透過包含\/排除設定停用載入**\]，您可以指示偵錯工具從 Microsoft 公用符號伺服器下載符號，或是從您電腦的符號目錄中載入符號。  如需詳細資訊，請參閱[指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
#### 若要手動載入符號  
  
1.  在 \[**模組**\] 視窗中，於未載入其符號的模組上按一下滑鼠右鍵。  
  
2.  指向 \[**載入符號來源**\]，然後按一下 \[**Microsoft 符號伺服器**\] 或 \[**符號路徑**\]。  
  
#### 若要變更符號載入設定  
  
1.  在 \[**模組**\] 視窗中，以滑鼠右鍵按一下任一模組。  
  
2.  按一下 \[**符號設定**\]。  
  
     現在您可以變更符號載入設定，如 [指定符號位置和載入行為](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior) 所說明。  在重新啟動偵錯工作階段之前，變更不會生效。  
  
#### 若要變更特定模組的符號載入行為  
  
1.  在 \[**模組**\] 視窗中，以滑鼠右鍵按一下模組。  
  
2.  指向 \[**自動符號載入設定**\]，然後按一下 \[**永遠手動載入**\] 或 \[**預設值**\]。  在重新啟動偵錯工作階段之前，變更不會生效。  
  
## 請參閱  
 [Breaking Execution](http://msdn.microsoft.com/zh-tw/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)