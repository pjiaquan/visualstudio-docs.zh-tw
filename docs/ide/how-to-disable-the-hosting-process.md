---
title: "如何：停用裝載處理序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "裝載處理序, 停用"
  - "vshost.exe, 停用裝載處理序"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：停用裝載處理序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

某些 API 的呼叫可能會在啟用裝載處理序 \(Hosting Process\) 時被影響。  在這些情況下，必須停用裝載處理序才能傳回正確的結果。  
  
### 若要停用裝載處理序  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中開啟可執行的專案。  不會產生可執行檔的專案 \(例如，類別庫或服務專案\) 沒有這個選項。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
3.  按一下 \[**偵錯**\] 索引標籤。  
  
4.  清除 \[**啟用 Visual Studio 裝載處理序**\] 核取方塊。  
  
 停止裝載處理序之後，會無法使用數項偵錯功能，或發生效能降低的情形。  如需詳細資訊，請參閱[偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)。  
  
 一般而言，當裝載處理序停用時：  
  
-   開始對 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 應用程式進行偵錯的時間會增加。  
  
-   設計階段運算式評估為無法使用。  
  
-   無法使用部分信任偵錯。  
  
## 請參閱  
 [偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)   
 [裝載處理序 \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/zh-tw/c9497d62-3b7b-4449-88e8-cf27acc9efe6)