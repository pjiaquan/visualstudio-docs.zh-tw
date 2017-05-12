---
title: "IScriptEntry::SetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetSignature"
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetSignature
設定 `IScriptEntry` 函式物件的型別資訊。  
  
## 語法  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### 參數  
 `pti`  
 \[in\] 型別資訊。  
  
 `iMethod`  
 \[in\] 在 `ITypeInfo` 物件方法的索引。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 您可以使用 `IScriptEntry::SetSignature` 或 [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)的集合型別資訊。  型別資訊可能會根據內部函式表示的項目也會產生。  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)