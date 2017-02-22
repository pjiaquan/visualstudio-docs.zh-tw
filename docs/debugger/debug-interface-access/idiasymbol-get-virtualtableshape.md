---
title: "IDiaSymbol::get_virtualTableShape | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualTableShape 方法"
ms.assetid: 92360cbd-0761-446e-93f9-04dc8f4b66c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualTableShape
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取符號的介面的虛擬資料表使用者定義型別的型別。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualTableShape (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表使用者定義型別的虛擬資料表。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)