---
title: "IDebugSessionProviderEx:CanJITDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:CanJITDebug
apilocation: scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugSessionProviderEx:CanJITDebug
判斷指定的處理序來偵錯與 Just\-In\-Time 偵錯。  
  
## 語法  
  
```  
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### 參數  
 `pid`  
 \[in\] 要偵錯之處理序的處理序識別項。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IDebugSessionProviderEx 介面](../../winscript/reference/idebugsessionproviderex-interface.md)