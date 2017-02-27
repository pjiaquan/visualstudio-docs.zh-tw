---
title: "IDiaSymbol::get_udtKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_udtKind 方法"
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的各種不同的使用者定義的型別 \(UDT\)。  
  
## 語法  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)指定的 UDT 類型的列舉型別： 結構、 類別或等位。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)