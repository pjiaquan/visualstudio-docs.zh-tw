---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
具有字串不是原本就可檢視傳回的文字是描述屬性的名稱，可顯示在呼叫端的使用者介面的顯示模式。  
  
## 語法  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### 參數  
 `dispid`  
 \[in\] 分派顯示名稱要求屬性的識別項。  
  
 `pBstr`  
 \[out\] 包含顯示名稱屬性的 `BSTR` 的指標 \(由所 `dispID`。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 備註  
 傳回的字串不是屬性的合法值。  這是屬性中顯示的字串。  
  
## 請參閱  
 [IPerPropertyBrowsing2 介面](../../winscript/reference/iperpropertybrowsing2-interface-1.md)