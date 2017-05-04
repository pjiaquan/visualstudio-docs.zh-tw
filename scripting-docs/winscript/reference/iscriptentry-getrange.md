---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
傳回項目的起始位置和長度。  
  
## 語法  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### 參數  
 `pichMin`  
 \[in\] 指定指令碼區塊的 `IScriptEntry` 物件，則會傳回 0。  
  
 如需指定函式物件的 `IScriptEntry` 物件，傳回函式的開始位置是在目前指令碼區塊。  
  
 對於 `IScriptScriptlet` 物件，則會傳回 0。  
  
 `pcch`  
 \[in\] 指定指令碼區塊的 `IScriptEntry` 物件，傳回文字的長度。  
  
 如需指定函式物件的 `IScriptEntry` 物件，會傳回函式定義的長度。  
  
 對於 `IScriptScriptlet` 物件，傳回項目的長度。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)