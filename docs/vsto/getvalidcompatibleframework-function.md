---
title: "GetValidCompatibleFramework 函式"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework 函式
  這個 API 支援 Office 基礎結構並不適合直接從程式碼使用。  
  
## 語法  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|*lpwszCompatibleFrameworksXML*|請不要使用。|  
|*pbstrValidFrameworkTag*|請不要使用。|  
  
## 傳回值  
 如果函式成功，則傳回 **S\_OK**。  如果函式失敗，則會傳回錯誤碼。  
  
  