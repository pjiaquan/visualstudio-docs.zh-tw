---
title: "編輯後繼續錯誤訊息對話方塊 | Microsoft Docs"
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
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "編輯後繼續錯誤訊息對話方塊"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 編輯後繼續錯誤訊息對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您使用支援 \[編輯後繼續\] 的語言進行偵錯，但 \[**編輯後繼續**\] 無法用於您所進行的程式碼變更類型時，這個對話方塊就會出現。  方塊內的錯誤訊息會提供更詳細的說明。  出現這個對話方塊的可能原因包括：  
  
-   您嘗試在已啟用 Unmanaged 偵錯時編輯 Managed 程式碼。  \[編輯後繼續\] 不會處理混合模式偵錯。  
  
-   您嘗試編輯 SQL Server 程式碼。  
  
-   您嘗試在下列項目進行偵錯時編輯程式碼：Dr.  Watson 傾印。  
  
-   您嘗試在發生未處理的例外狀況之後編輯程式碼，但是並未選取 \[**發生未處理的例外狀況時回溯呼叫堆疊**\] 選項。  
  
-   您嘗試在進行內嵌執行階段應用程式偵錯時編輯程式碼。  
  
-   您嘗試在附加程式碼的程式中，而不是從 \[**偵錯**\] 功能表啟動的程式中編輯程式碼。  
  
-   您嘗試編輯最佳化程式碼。  
  
-   您嘗試在目標為 64 位元應用程式時編輯 Managed 程式碼。  如果要使用 \[編輯後繼續\]，就必須將目標設定為 x86 \(依序選取 \[**進階編譯器設定**\]、\[**編譯**\] 索引標籤、\[*Project* **屬性**\]\)。  
  
-   您嘗試在已於偵錯期間修改且已重新載入的組譯碼中編輯程式碼。  
  
-   您嘗試編輯尚未載入之組譯碼中的程式碼。  
  
-   您已開始偵錯舊版的應用程式 \(因為新版本有建置錯誤\)。  
  
-   您嘗試在程式碼正在執行時編輯該程式碼。  
  
## UIElement 清單  
 **OK**  
 結束對話方塊，並取消緊接在前的編輯嘗試。  
  
## 請參閱  
 [支援的程式碼變更及限制 \(C\+\+\)](../debugger/supported-code-changes-cpp.md)