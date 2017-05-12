---
title: "IRemoteDebugApplication::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CauseBreak
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CauseBreak"
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication::CauseBreak
會對應用程式有機會進入偵錯工具。  
  
## 語法  
  
```  
HRESULT CauseBreak();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 呼叫這個方法不會導致應用程式立即中斷。  如果應用程式目前並未執行指令碼，很長的時間可能會超過，在應用程式實際中斷之前。  
  
## 請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)