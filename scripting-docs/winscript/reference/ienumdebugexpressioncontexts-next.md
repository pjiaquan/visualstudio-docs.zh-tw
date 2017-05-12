---
title: "IEnumDebugExpressionContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Next"
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Next
擷取區段的指定數目在列舉型別序列中  
  
## 語法  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] 要擷取的區段數目。  
  
 `ppdec`  
 \[in\] 傳回表示擷取的區段的陣列 `IDebugExpressionContext` 介面。  
  
 `pceltFetched`  
 \[in\] 列舉值擷取的區段的實際數目。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會擷取區段的指定數目在列舉型別序列中  
  
## 請參閱  
 [IEnumDebugExpressionContexts 介面](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)