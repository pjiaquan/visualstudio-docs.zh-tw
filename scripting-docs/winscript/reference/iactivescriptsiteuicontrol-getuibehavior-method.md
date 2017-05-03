---
title: "IActiveScriptSiteUIControl::GetUIBehavior 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior 方法
取得表示方法應該處理 UI 控制項的 [SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md) 。  
  
## 語法  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### 參數  
 `UicItem`  
 控制項的型別。  
  
 `pUicHandling`  
 如果應該處理這個控制項模式。