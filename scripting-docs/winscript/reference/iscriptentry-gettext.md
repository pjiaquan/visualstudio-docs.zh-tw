---
title: "IScriptEntry::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetText"
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetText
傳回對應於 `IScriptEntry` 指令碼區塊的文字，或在 `IScriptScriptlet` 事件處理常式中的原始程式碼。  
  
## 語法  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### 參數  
 `pbstr`  
 \[in\] 在 `IScriptEntry` 指令碼區塊的文字或在 `IScriptScriptlet` 事件處理常式中的原始程式碼。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)