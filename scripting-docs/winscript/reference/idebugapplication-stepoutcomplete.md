---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
告知同處理序偵錯管理員以語言引擎在單一步驟模式會傳回給呼叫端。  
  
## 語法  
  
```  
HRESULT StepOutComplete();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 包含設定回其呼叫端之前，語言引擎在單一步驟模式中呼叫這個方法。  同處理序偵錯處理常式使用機會告知其他指令碼引擎它們應中斷在第一個機會。  這項技術是跨語言步驟模式是如何實作。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)