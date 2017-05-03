---
title: "JsDebugPropertyInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsDebugPropertyInfo 結構
指出有關屬性的資訊。  
  
## 語法  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## Members  
 `name`  
 屬性的名稱。  
  
 `type`  
 屬性的型別。  
  
 `value`  
 屬性的值。  
  
 `fullName`  
 屬性的完整名稱。  
  
 `attr`  
 表示屬性的列舉屬性。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)