---
title: "IDiaSymbol::get_virtual | Microsoft Docs"
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
  - "IDiaSymbol::get_virtual 方法"
ms.assetid: 97e3ad51-8ef3-4446-ab33-3cb34a21b7a0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtual
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定是否為虛擬的函式。  
  
## 語法  
  
```cpp#  
HRESULT get_virtual (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果函式是虛擬的。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)