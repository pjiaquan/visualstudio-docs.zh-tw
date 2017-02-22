---
title: "IDiaSymbol::get_machineType | Microsoft Docs"
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
  - "IDiaSymbol::get_machineType 方法"
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_machineType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取目標 CPU 的型別。  
  
## 語法  
  
```cpp#  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)指定目標 CPU 類型的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)