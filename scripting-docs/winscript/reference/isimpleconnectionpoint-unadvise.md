---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
結束先前透過 `ISimpleConnectionPoint::Advise` 建立的諮詢連接。  
  
## 語法  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### 參數  
 `dwCookie`  
 \[in\] 結束連接的語彙基元，所傳回。 `ISimpleConnectionPoint::Advise`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 當諮詢連接結束時，連接點會在 `ISimpleConnectionPoint::Advise` 方法期間，用於連接已儲存之指標的 `Release` 方法。  執行 `ISimpleConnectionPoint::Advise` 的該呼叫反轉 `AddRef` ，當連接點呼叫通知接收的 `QueryInterface`時。  
  
## 請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)