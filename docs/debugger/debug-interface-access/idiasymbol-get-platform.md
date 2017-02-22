---
title: "IDiaSymbol::get_platform | Microsoft Docs"
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
  - "IDiaSymbol::get_platform 方法"
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的編譯時所編譯的平台類型。  
  
## 語法  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)指定的平台的列舉型別編譯時所編譯。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)