---
title: "錯誤：RPC 需要驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 錯誤：RPC 需要驗證
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 偵錯工具無法連接至遠端電腦。  本機電腦上啟用了 RPC 原則，會阻止遠端偵錯進行。  
  
### 若要更正這個錯誤  
  
1.  執行 `\`*windir*`\system32\regedt32.exe`  
  
2.  找出並刪除 `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`。  
  
3.  重新啟動您的電腦，如此登錄變更才會生效。  
  
4.  如果問題仍然存在，請洽詢網域管理員有關 \[電腦設定\]\-\>\[系統管理範本\]\-\>\[系統\]\-\>\[遠端程序呼叫\]\-\>\[未經驗證的 RPC 用戶端限制\] 的群組原則設定。