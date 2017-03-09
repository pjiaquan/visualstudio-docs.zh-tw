---
title: "錯誤：無法連接至電腦 &lt;name&gt;。網路上找不到這部電腦。 | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, 無法連接錯誤"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：無法連接至電腦 &lt;name&gt;。網路上找不到這部電腦。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果下列其中一種情況為 true 時，就會發生這個行為：  
  
-   與遠端電腦的連線中斷。  
  
-   在遠端電腦上的使用者帳戶已停用。  
  
-   遠端電腦上的密碼已到期。  
  
### 若要解決這個行為  
  
-   請確定本機電腦與遠端電腦位於相同的網路上。  方法是，使用 Microsoft Windows \[檔案總管\] \(或 \[檔案總管\]\) 嘗試存取遠端電腦。  
  
     \-和\-  
  
-   請確定已啟用您用以連接遠端電腦的使用者帳戶。  
  
     \-和\-  
  
-   請確定您用以連接遠端電腦的密碼是有效的，而且尚未到期。  
  
## 請參閱  
 [在裝置上設定遠端工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)