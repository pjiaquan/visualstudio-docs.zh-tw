---
title: "如何：使用暫存器視窗 | Microsoft Docs"
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
  - "vs.debug.registers"
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
  - "暫存器, 偵錯"
  - "暫存器內容"
  - "旗標, [暫存器] 視窗"
  - "暫存器群組"
  - "偵錯 [Visual Studio], [暫存器] 視窗"
  - "暫存器視窗"
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用暫存器視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只有在透過 \[**選項**\] 對話方塊 \[**一般**\] 分類的 \[**偵錯**\] 節點啟用位址層級偵錯時，才可以使用 \[暫存器\] 視窗。  
  
 \[**暫存器**\] 視窗會顯示暫存器內容。  如果您在逐步進行程式的時候讓 \[**暫存器**\] 視窗保持開啟，您可以察看程式碼執行時暫存器值的變更。  最近變更過的值以紅色顯示。  您可以編輯暫存器值。  如需詳細資訊，請參閱 [如何：編輯暫存器值](../debugger/how-to-edit-a-register-value.md)。  
  
 若要減少雜亂的情況，\[**暫存器**\] 視窗會依據平台和處理器類型將暫存器組成不同的群組。  您可以視需要顯示或隱藏群組。  如需詳細資訊，請參閱 [如何：顯示和隱藏暫存器群組](../debugger/how-to-display-and-hide-register-groups.md)。  
  
 如需暫存器和 \[暫存器\] 視窗的高階簡介及概念，請參閱[偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要顯示暫存器視窗  
  
-   在 \[**偵錯**\] 功能表上，選擇 \[**視窗**\]，然後選擇 \[**暫存器**\]。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
    > [!NOTE]
    >  暫存器資訊無法用於指令碼或 SQL 應用程式內。  
  
## 請參閱  
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [偵錯基本概念：暫存器視窗](../debugger/debugging-basics-registers-window.md)