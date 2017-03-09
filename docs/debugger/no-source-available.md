---
title: "沒有可用來源 | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "沒有目前位置可用的原始程式碼對話方塊"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 沒有可用來源
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您的專案未包含您嘗試檢視之程式碼的原始程式碼。  常見的原因是在 \[**呼叫堆疊視窗**\] 或 \[**執行緒視窗**\] 中按兩下沒有原始程式碼的模組。  您可以繼續偵錯，但無法使用來源視窗設定中斷點，或是在此位置執行其他動作。  如果您需要設定中斷點，請改用 \[**反組譯碼視窗**\]。  
  
 在 \[方案屬性頁\] 中，您可以變更偵錯工具搜尋原始程式檔的目錄，並告知偵錯工具忽略選取的原始程式檔。  請參閱 [方案屬性頁對話方塊、通用屬性、偵錯原始程式檔](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。  
  
 **瀏覽以尋找原始程式碼**  
 按一下這個連結開啟對話方塊，您可以在其中瀏覽以尋找原始程式碼。  
  
 **顯示反組譯碼**  
 啟動 \[**反組譯碼視窗**\]。  
  
 **對遺漏的原始程式檔永遠顯示反組譯碼**  
 選取這個選項會在沒有原始程式碼時，自動顯示 \[**反組譯碼視窗**\]。  這項設定也可以在 \[**選項**\] 對話方塊、\[**偵錯**\] 分類、\[**一般**\] 頁面中，透過選取或清除 \[**找不到原始碼時則顯示反組譯碼**\] 的方式變更。  
  
## 請參閱  
 [方案屬性頁對話方塊、通用屬性、偵錯原始程式檔](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)