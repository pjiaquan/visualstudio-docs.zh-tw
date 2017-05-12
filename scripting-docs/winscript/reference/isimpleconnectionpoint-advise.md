---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
建立簡單的連接點物件和用戶端的接收之間的連接。  
  
## 語法  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### 參數  
 `pdisp`  
 \[out\] 介面的指標 `IDispatch` 用戶端上的通知接收。  用戶端的接收收到來自簡單連接點的傳出呼叫。  
  
 `pdwCookie`  
 \[out\] 可唯一識別此連接的傳回的語彙基元的指標。  呼叫端之後使用語彙基元傳遞給刪除連接至 `ISimpleConnectionPoint::Unadvise` 方法。  如果連接成功建立，這個值是零。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立簡單的連接點物件和用戶端的接收之間的連接。  
  
## 請參閱  
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)