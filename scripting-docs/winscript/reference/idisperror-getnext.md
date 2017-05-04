---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
擷取下一 `IDispError` 物件。  
  
## 語法  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### 參數  
 `ppde`  
 \[in\] 指定下 `IDispError` 物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會擷取下一 `IDispError` 物件。  如果這是最後一個 `IDispError` 物件，這個方法會傳回 NULL。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## 請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)