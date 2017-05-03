---
title: "DebugPropertyInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo 結構"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo 結構
描述具有名稱、型別和值的階層式性質的物件。  它是用來描述區域變數偵錯屬性、參數、監看式變數和運算式和暫存器。  
  
## 語法  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## Members  
 dwValidFields  
 用來列舉資料型別指定哪些欄位初始化。  
  
 bstrName  
 在內容中的屬性名稱。  
  
 bstrType  
 屬性型別，做為格式化字串。  
  
 bstrValue  
 屬性值，做為格式化字串。  
  
 bstrFullName  
 屬性的完整名稱。  
  
 dwAttrib  
 提供偵錯屬性旗標列舉型別的屬性。  
  
 pDebugProp  
 描述資訊的 `IDebugProperty` 在這 `DebugPropertyInfo` 結構。  
  
## 請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)