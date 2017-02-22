---
title: "IDiaSymbol::get_volatileType | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_volatileType 方法"
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_volatileType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定使用者自訂資料型別 \(UDT\) 是否為動態的旗標。  
  
## 語法  
  
```cpp#  
HRESULT get_volatileType (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果 UDT 是暫時性的。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 可以使用標記 UDT C\+\+ `volatile`關鍵字，指示它的內容無法被假設有一個存取下一步\]。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)