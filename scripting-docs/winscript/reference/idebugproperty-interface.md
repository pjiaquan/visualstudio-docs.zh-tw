---
title: "IDebugProperty 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty 介面"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty 介面
用來描述具有名稱、型別和值所偵錯之實體的任何階層式屬性。  通常， `IDebugProperty` 用來描述運算式評估、陳述式評估或暫存器評估的結果。  
  
## 依照 Vtable 順序的方法  
 下表顯示 `IDebugProperty` 介面的方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|取得描述這 `IDebugProperty``.`的 `DebugPropertyInfo`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|取得有關屬性的擴充資訊。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|設定屬性的值從字串。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|列舉型別屬性的成員。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|取得屬性的父代。|  
  
## 需求  
 標題:dbgprop.h