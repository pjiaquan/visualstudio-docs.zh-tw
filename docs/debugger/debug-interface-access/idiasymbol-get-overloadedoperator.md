---
title: "IDiaSymbol::get_overloadedOperator | Microsoft Docs"
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
  - "IDiaSymbol::get_overloadedOperator 方法"
ms.assetid: 257a9894-e980-47ae-bdc0-c5e2293ea734
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_overloadedOperator
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定使用者自訂資料型別是否具有多載運算子。  
  
## 語法  
  
```cpp#  
HRESULT get_overloadedOperator (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果使用者自訂資料型別具有多載的運算子。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)