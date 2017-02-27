---
title: "如何：編輯暫存器值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.register.edit"
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
  - "暫存器值"
  - "暫存器視窗, 編輯暫存器值"
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：編輯暫存器值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只有在透過 \[**選項**\] 對話方塊的 \[**偵錯**\] 節點啟用位址層級偵錯時，才可以使用 \[暫存器\] 視窗。  
  
### 若要變更暫存器值  
  
1.  您可以在 \[**暫存器**\] 視窗中使用 TAB 鍵或滑鼠，將插入點移至要變更的值上。  輸入時，游標必須放在要覆寫的值的前面。  
  
2.  輸入新值。  
  
    > [!CAUTION]
    >  變更暫存器值 \(尤其是 EIP 和 EBP 暫存器中的值\) 會影響程式執行。  
  
    > [!CAUTION]
    >  由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。  即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。  
  
## 請參閱  
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)