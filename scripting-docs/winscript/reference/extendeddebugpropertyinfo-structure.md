---
title: "ExtendedDebugPropertyInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo 結構"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo 結構
擴充 `DebugPropertyInfo` 結構與其他成員 Draw 擴充屬性。  
  
## 語法  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## Members  
 `dwValidFields`  
 用來列舉資料型別指定哪些欄位初始化。  
  
 `bstrName`  
 在內容中的屬性名稱。  
  
 `bstrType`  
 做為格式化字串的屬性型別。  
  
 `bstrValue`  
 屬性值做為格式化字串。  
  
 `bstrFullName`  
 屬性的完整名稱。  
  
 `dwAttrib`  
 提供偵錯屬性旗標列舉型別的屬性。  
  
 `pDebugProp`  
 與這個 `ExtendedDebugPropertyInfo`的`IDebugProperty` 物件。  
  
 `nDISPID`  
 分派 ID.  
  
 `nType`  
 擴充屬性型別。  
  
 `varValue`  
 擴充屬性值，則無法納入 Variant。  
  
 `plbValue`  
 屬性值的實際資料位元組。  
  
 `pDebugExtProp`  
 與這個 `ExtendedDebugPropertyInfo`的`IDebugExtendedProperty` 物件。  
  
## 請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)