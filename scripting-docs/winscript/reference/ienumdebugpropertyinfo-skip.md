---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
略過 `DebugPropertyInfo` 結構的指定數目在列舉型別序列的。  
  
## 語法  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] `DebugPropertyInfo` 結構數目略過列舉型別序列的。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  傳回 `S_FALSE` 並將目前項目指標設定為列舉型別的結尾，則 `celt` 比列舉值中的元素數目大於。  
  
## 請參閱  
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)