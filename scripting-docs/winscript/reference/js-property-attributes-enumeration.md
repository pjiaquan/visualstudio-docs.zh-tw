---
title: "JS_PROPERTY_ATTRIBUTES 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JS_PROPERTY_ATTRIBUTES 列舉
指出屬性 \(Property\) 的屬性 \(Attribute\)。  
  
## 語法  
  
```  
enum JS_PROPERTY_ATTRIBUTES  
{  
   JS_PROPERTY_ATTRIBUTE_NONE = 0,  
   JS_PROPERTY_HAS_CHILDREN = 0x1,  
   JS_PROPERTY_FAKE = 0x2,  
   JS_PROPERTY_METHOD = 0x4,  
   JS_PROPERTY_READONLY = 0x8,  
   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10  
} JS_PROPERTY_ATTRIBUTES;  
```  
  
## Members  
  
|名稱|描述|  
|--------|--------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|屬性沒有屬性。|  
|`JS_PROPERTY_HAS_CHILDREN`|屬性具有子系。|  
|`JS_PROPERTY_FAKE`|屬性表示假的節點，例如「方法」。|  
|`JS_PROPERTY_METHOD`|屬性是方法。|  
|`JS_PROPERTY_READONLY`|屬性是唯讀的。|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|屬性是指向原生 WinRT 物件。|  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)