---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
傳回對應於 `IScriptEntry` 指令碼區塊、區塊或 scriptlet 函式主體中的文字。  
  
## 語法  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### 參數  
 `pbstr`  
 \[in\] 在主體以下其中一種文字:  
  
-   `IScriptEntry` 指令碼區塊  
  
-   在函式執行區塊中的 `IScriptEntry` 函式  
  
-   `IScriptEntry` scriptlet 事件處理常式  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)