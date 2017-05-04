---
title: "IDispError::QueryErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::QueryErrorInfo"
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::QueryErrorInfo
擷取錯誤訊息的特定型別。  
  
## 語法  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### 參數  
 `guidErrorType`  
 \[in\] 指定錯誤類型的 GUID。  
  
 `ppde`  
 \[in\] 指定 IDispError 物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 `QueryErrorInfo` 方法擷取錯誤訊息的特定型別。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## 請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)