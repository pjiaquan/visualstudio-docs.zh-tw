---
title: "IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveNamedItem"
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::RemoveNamedItem
從建立的指令碼引擎的命名空間 `NamedItem` 移除物件。  
  
## 語法  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### 參數  
 `pszName`  
 \[in\] 識別 `NamedItem` 物件移除緩衝區的位址。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|`NamedItem` 物件不存在於建立的指令碼引擎的命名空間。|  
  
## 備註  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 用來插入至物件 `NamedItem` 撰寫引擎的命名空間的指令碼。  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)