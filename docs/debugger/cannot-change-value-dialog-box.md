---
title: "無法變更值對話方塊 | Microsoft Docs"
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
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "無法變更值對話方塊"
  - "變數 [偵錯工具], 編輯"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 無法變更值對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 錯誤  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 當您在偵錯工具視窗 \(\[自動變數\]、\[監看式\] 或 \[區域變數\] 視窗\) 或 \[快速監看式\] 對話方塊中嘗試將變數內容變更為無效值時，這個訊息方塊就會出現。  例如，如果您將整數變數的值設定成字元字串，這個訊息方塊就會出現。  
  
## 解決方案  
 確認您輸入偵錯工具視窗或 \[快速監看式\] 對話方塊內的輸入內容，對於您嘗試設定的變數而言是有效的值。  
  
## 請參閱  
 [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)