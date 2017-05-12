---
title: "IActiveScriptTraceInfo::StartScriptTracing 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing 方法
啟動指令碼追蹤。  
  
## 語法  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### 參數  
 `pSiteTraceInfo`  
 out 主應用程式的 IActiveScriptSiteTraceInfo 的指標。  
  
 `guidContextId`  
 內容的 GUID。  
  
## 傳回值  
 這個方法傳回的可能值如下:  
  
1.  S\_OK:成功。  
  
2.  E\_POINTER: `pSiteTraceInfo` 是 null 指標。  
  
3.  E\_NOTIMPL:尚未實作。