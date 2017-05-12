---
title: "SetWefProcessId 方法"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId 方法
  提供會執行 Web Extension Framework \(WEF\) 內容的處理序識別項。  
  
## 語法  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|*dwProcessId*|要用來執行 WEF 內容的處理序識別項。|  
  
## 傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## 備註  
 必須先呼叫這個方法，在 WEF 內容流程建立之後，但在中，所有 WEF 內容執行之前。  
  
 如果您要開發環境將偵錯工具附加至 WEF 內容流程，環境在這個方法的實作必須執行這項作業。  
  
  