---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
允許呼叫端使用計數的陣列表示此屬性的可能值的字串指標填入清單方塊。  
  
## 語法  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### 參數  
 `dispid`  
 \[in\] 分派呼叫端要求字串清單屬性的識別項。  
  
 `pCaStrings`  
 \[out\] 包含配置的陣列元素計數和地址資料指標的呼叫端配置的，計數的陣列的結構的指標。  如果方法失敗，並不會配置記憶體，因此，結構的內容是未定義的。  
  
 `pCaCookies`  
 \[out\] 包含一個方法所配置的陣列元素計數和位址 DWORDs 的呼叫端配置的，計數的陣列的結構的指標。  如果方法失敗，並不會配置記憶體，因此，結構的內容是未定義的。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IPerPropertyBrowsing2 介面](../../winscript/reference/iperpropertybrowsing2-interface-1.md)