---
title: "SCRIPTGCTYPE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE 列舉
執行記憶體回收的類型。  在 [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) 方法中使用。  
  
## 語法  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|一般進行記憶體回收。  整數值是 0。|  
|SCRIPTGCTYPE\_EXHAUSTIVE|進行完整的記憶體回收。  整數值是 1。|  
  
## 請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)