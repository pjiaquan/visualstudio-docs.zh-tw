---
title: "EnsureVSTOComponent 函式 | Microsoft Docs"
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
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# EnsureVSTOComponent 函式
  這個 API 支援 Office 基礎結構並不適合直接從程式碼使用。  
  
## 語法  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|*pProject*|請不要使用。|  
  
## 傳回值  
 如果函式成功，則傳回 **S\_OK**。  如果函式失敗，則會傳回錯誤碼。  
  
  