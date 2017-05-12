---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
物件 `IScriptEntry` 函式的傳回型別資訊。  
  
## 語法  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### 參數  
 `ppti`  
 \[in\] 輸入資訊與這個 `IScriptEntry` 函式物件。  
  
 `piMethod`  
 \[in\] 在 `ITypeInfo` 物件方法的索引。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 您可以使用 [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) 或 [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)的集合型別資訊。  型別資訊可能會根據內部函式表示的項目也會產生。  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)