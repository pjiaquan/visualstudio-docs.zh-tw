---
title: "IDiaSymbol::get_virtualBasePointerOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualBasePointerOffset 方法"
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualBasePointerOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取虛擬基底指標的位移。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回虛擬基底指標的位移。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)