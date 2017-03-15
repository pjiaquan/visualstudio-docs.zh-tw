---
title: "過時程式碼警告對話方塊 | Microsoft Docs"
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
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "過時程式碼警告對話方塊"
  - "程式碼, 過時程式碼警告"
  - "警告, [過時程式碼警告] 對話方塊"
  - "編輯後繼續, 過時程式碼"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 過時程式碼警告對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您對 \[**編輯後繼續**\] 無法立即套用的機器碼進行變更時，這個對話方塊就會出現。  因此，現在目前堆疊框架中的某些機器碼已過期，也就是過時了。  如需詳細資訊，請參閱[How to: Work with Stale Code](http://msdn.microsoft.com/zh-tw/c7536e95-66a6-44a0-995d-3fe5035250b4)。  
  
 **不要再顯示此對話方塊**  
 如果選取這個核取方塊，\[編輯後繼續\] 以後將直接套用程式碼變更，並且不再請求允許變更。  您可以在 \[**選項**\] 對話方塊中開啟 \[**偵錯**\] 資料夾，按一下 \[**編輯後繼續**\] 頁面，然後選取 \[**警告出現過時的程式碼**\]，即可重新開啟這個警告。  
  
## 請參閱  
 [支援的程式碼變更及限制 \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [選項對話方塊、偵錯、編輯後繼續](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)