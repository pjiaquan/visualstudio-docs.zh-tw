---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
列舉型別屬性的成員。  
  
## 語法  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### 參數  
 `dwFieldSpec`  
 \[in\] 指定的 `DBGPROP_INFO_FLAGS` 常數的哪些欄位是列舉的偵錯屬性結構就會填入。  
  
 `nRadix`  
 \[in\] 用來解譯任何數字資訊的基數。  
  
 `refiid`  
 \[in\] 這個 IID 所篩選的列舉值傳遞。  IID 是從 `IDebugPropertyEnumType_All`繼承的其中一 `IDebugPropertyEnumType` 介面。  
  
 `ppEnum`  
 \[in\] 傳回列舉型別成員屬性的 `IEnumDebugPropertyInfo` 介面。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType\_All 介面](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)