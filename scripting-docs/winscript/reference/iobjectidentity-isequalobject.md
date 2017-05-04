---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject 方法"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
判斷物件是否等於目前的物件。  
  
## 語法  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### 參數  
 `punk`  
 \[out\] 物件的位址與目前物件比較的物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|物件。|  
|`S_FALSE`|物件不相等。|  
  
## 備註  
 只有在物件相同， `IsEqualObject` 方法的實作應該會傳回 `S_OK` 。  
  
## 請參閱  
 [IObjectIdentity 介面](../../winscript/reference/iobjectidentity-interface.md)