---
title: "IDiaSymbol::get_virtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualAddress 方法"
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取虛擬位址 \(VA\) 的位置。  何時使用[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 \[ `LocIsStatic`。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回虛擬位址的位置。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)