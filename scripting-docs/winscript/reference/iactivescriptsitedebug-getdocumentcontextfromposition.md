---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
由語言引擎 `IDebugCodeContext::GetSourceContext`委派。  
  
## 語法  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### 參數  
 `dwSourceContext`  
 \[in\] 來源內容所提供的 `ParseScriptText` 或 `AddScriptlet`。  
  
 `uCharacterOffset`  
 \[in\] 指令碼區塊或 scriptlet 字元位移相對於起始。  
  
 `uNumChars`  
 \[in\] 字元的數字在此內容中。  
  
 `ppsc`  
 \[in\] 與此字元位置到範圍的文件內容。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 語言引擎使用這個方法 `IDebugCodeContext::GetSourceContext`委派。  
  
## 請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)