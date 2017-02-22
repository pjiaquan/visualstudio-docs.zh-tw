---
title: "偵錯工作階段的可執行檔對話方塊 | Microsoft Docs"
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
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "可執行檔, 偵錯時指定"
  - "DLL, 偵錯"
  - "偵錯工具, [偵錯工作階段的可執行檔] 對話方塊"
  - "偵錯工作階段的可執行檔對話方塊"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯工作階段的可執行檔對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您嘗試對未指定任何可執行檔的 DLL 進行偵錯時，就會出現這個對話方塊。  Visual Studio 無法直接啟動 DLL。  它會改為啟動指定的可執行檔。  您可以對可執行檔呼叫的 DLL 進行偵錯。  
  
 **可執行檔名稱**  
 輸入呼叫您要進行偵錯之 DLL 的可執行檔路徑名稱。  
  
 **可以存取專案的 URL，僅限 ATL Server**  
 如果您要對 ATL 伺服器 DLL 進行偵錯，請輸入可以找到專案的 URL。  
  
 輸入後，這些設定都會儲存在專案的 \[屬性頁\] 中，如此就不必在後續偵錯工作階段中重新輸入。  如果您需要變更設定，請開啟 \[屬性頁\] 並變更這些值。  如需為偵錯工作階段指定可執行檔的詳細資訊，請參閱[偵錯 DLL](../Topic/How%20to:%20Debug%20Native%20DLLs.md)。  
  
## 請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)