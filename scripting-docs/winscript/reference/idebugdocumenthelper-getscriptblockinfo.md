---
title: "IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetScriptBlockInfo
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetScriptBlockInfo"
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetScriptBlockInfo
擷取字元和指令碼引擎的範圍與指令碼區塊對應。  
  
## 語法  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### 參數  
 `dwSourceContext`  
 \[in\] 指令碼區塊的來源內容。  
  
 `ppasd`  
 \[out\] 此指令碼區塊的指令碼引擎。  
  
 `piCharPos`  
 \[in\] 指令碼區塊的開始位置。  
  
 `cChars`  
 \[in\] 字元數量的指令碼區塊。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會擷取字元和指令碼引擎的範圍與指令碼區塊對應。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)