---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
略過區段的指定數目在列舉型別序列中  
  
## 語法  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] 區段個數略過列舉型別序列的。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會略過區段的指定數目在列舉型別序列中  
  
## 請參閱  
 [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)