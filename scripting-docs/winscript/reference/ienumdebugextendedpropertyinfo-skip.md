---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
略過 `ExtendedDebugPropertyInfo` 結構的指定數目在列舉型別序列的。  
  
## 語法  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] `ExtendedDebugPropertyInfo` 結構數目略過列舉型別序列的。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  傳回 `S_FALSE` 並將目前項目指標設定為列舉型別的結尾，則 `celt` 比列舉值中的元素數目大於。  
  
## 請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)