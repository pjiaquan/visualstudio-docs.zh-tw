---
title: "IPerPropertyBrowsing2 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 介面"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2 介面
存取物件中提供的屬性頁的詳細資訊。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|`GetDisplayString`|傳回描述指定之屬性的文字字串。|  
|`MapPropertyToPage`|傳回可以指定屬性的作業屬性頁的 CLSID。|  
|`GetPredefinedStrings`|傳回清單中指定的屬性可以接受允許值的描述的計數的字串陣列 \(`LPOLESTR` 指標\)。|  
|`SetPredefinedValue`|設定屬性的值設定為 `dwCookie.`語彙基元所識別的預先定義值。|  
  
## 需求  
 標題:dbgprop.h