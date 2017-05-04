---
title: "GetAutoInsertExtensions 方法 | Microsoft Docs"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions 方法
  取得有關在偵錯期間，要自動插入的應用程式資訊的 Office 專案中。  
  
 這個方法保留給未來的版本使用。  
  
## 語法  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|*psaExtensionNames*|應用程式的擴充 Office 的名稱。|  
  
## 傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## 備註  
 要插入的 Office 的每個應用程式會以 Office 應用程式擴充名稱，對應於的值。\\Software\\Microsoft\\Office\\WEF\\Developer HKEY\_CURRENT\_USER 之下。  主應用程式必須搜尋登錄中的這些值會自動將標題副檔名。  
  
  