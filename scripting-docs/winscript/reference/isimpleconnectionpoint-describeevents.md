---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
傳回物件和名稱中的每個事件在事件中指定的範圍。  
  
## 語法  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### 參數  
 `iEvent`  
 \[in\] 要擷取之第一個事件的索引。  
  
 `cEvents`  
 \[in\] 要擷取的事件數目。  
  
 `prgid`  
 \[in\] 事件的 DISPID 值。  
  
 `prgbstr`  
 \[in\] 事件名稱。  
  
 `pcEventsFetched`  
 \[in\] 要擷取的實際事件數目。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|多個事件比可用的要求。  無法使用的事件會 DISPID\_NULL 和空 BSTR 表示。|  
|`E_INVALIDARG`|項目不能被擷取。|  
  
## 備註  
 這個方法會傳回物件和名稱中的每個事件在事件中指定的範圍。  
  
## 請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)