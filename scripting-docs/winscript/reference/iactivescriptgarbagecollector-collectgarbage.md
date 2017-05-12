---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
現用指令碼載入呼叫這個方法來開始進行記憶體回收。  
  
## 語法  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### 參數  
 `scriptgctype`  
 \[in\] 指定是否要執行一般或完整的記憶體回收的 [SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md) 。  
  
## 傳回值  
 傳回 HRESULT。  
  
## 請參閱  
 [IActiveScriptGarbageCollector 介面](../../winscript/reference/iactivescriptgarbagecollector-interface.md)