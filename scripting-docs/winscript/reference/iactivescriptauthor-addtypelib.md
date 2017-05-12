---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
將型別程式庫加入至指令碼的命名空間。  
  
## 語法  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### 參數  
 `rguidTypeLib`  
 \[in\] CLSID \(類別識別項\) 會將型別的程式庫。  
  
 `dwMajor`  
 \[in\] 主要版本號碼。  
  
 `dwMinor`  
 \[in\] 次要版本號碼。  
  
 `dwFlags`  
 \[in\] 不適用。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 呼叫這個方法 `LoadTypeLib` 載入型別程式庫。  在成功，這個方法會 `IActiveScriptAuthor::AddNamedItem` 將型別資訊。  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/zh-tw/155b48e5-5438-409e-9342-630a6a500f60)