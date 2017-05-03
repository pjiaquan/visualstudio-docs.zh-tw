---
title: "IDebugPropertyEnumType_All 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All 介面"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All 介面
`IDebugPropertyEnumType` 介面定義，使其每個 IID 可以做為篩選條件加入至 `IDebugProperty::EnumMembers` ，當要求適當的列舉值時。  
  
## 語法  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|傳回描述該名稱的文字字串。|  
  
 下列 `IDebugPropertyEnumType_All`介面從繼承，而且沒有其他方法。  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## 請參閱  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)