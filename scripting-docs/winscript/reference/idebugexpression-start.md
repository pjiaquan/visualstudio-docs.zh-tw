---
title: "IDebugExpression::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Start"
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Start
啟動這個運算式的評估。  
  
## 語法  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### 參數  
 `pdecb`  
 \[in\] 值的運算式評估何時完成的回呼。  如果此參數為 `NULL`，則不會引發事件。您可以使用 `QueryIsComplete`，因此，用戶端必須輪詢運算式狀態。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會啟動這個運算式的評估。  
  
## 請參閱  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)