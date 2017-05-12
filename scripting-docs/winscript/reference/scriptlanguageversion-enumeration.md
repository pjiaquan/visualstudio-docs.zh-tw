---
title: "SCRIPTLANGUAGEVERSION 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION 列舉
指定可能的指令碼的版本。  
  
## 語法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|預設版本。  整數值是 0。|  
|SCRIPTLANGUAGEVERSION\_5\_7|指令碼第 5.7 版的視窗。  整數值是 1。|  
|SCRIPTLANGUAGEVERSION\_5\_8|指令碼第 5.8 版的視窗。  整數值是 2。|  
|SCRIPTLANGUAGEVERSION\_MAX|最高版本。  整數值是 255。|  
  
## 請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)