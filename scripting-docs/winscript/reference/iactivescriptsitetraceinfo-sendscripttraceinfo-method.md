---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法
傳送包含事件型別、內容和指令碼陳述式的追蹤資訊。  
  
## 語法  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### 參數  
 `stiEventType`  
 事件型別。  
  
 `guidContextId`  
 內容的 GUID。  
  
 `dwScriptContextCookie`  
 內容的 Cookie。  
  
 `lScriptStatementStart`  
 指令碼陳述式的起始位置。  
  
 `lScriptStatementEnd`  
 指令碼陳述式的結尾的位置。  
  
 `dwReserved`  
 保留的。