---
title: "檔案追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 檔案追蹤"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 檔案追蹤
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

檔案追蹤會記錄處理序及其子處理序對 Windows 檔案系統的呼叫。  程式會藉由呼叫下列函式，控制開啟和關閉這項記錄功能的時機，並指定要使用的記錄檔。  
  
## 在本節中  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 停止追蹤目前的內容。  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 在呼叫 [SuspendTracking](../msbuild/suspendtracking.md) 之後繼續追蹤。  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 設定要用於追蹤的執行緒數目。  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 開始新的追蹤內容。  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 使用指定的根目錄開始新的追蹤內容。  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 結束追蹤並釋放使用的資源。  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 暫時停止追蹤。  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 寫出所有內容的追蹤記錄。  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 寫出目前內容的追蹤記錄。