---
title: "IDiaSymbol::get_hasSetJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSetJump 方法"
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasSetJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的函式是否包含一種使用其中一個旗標[setjmp](/visual-cpp/c-runtime-library/reference/setjmp)命令 \(與放大的成對[longjmp](/visual-cpp/c-runtime-library/reference/longjmp)命令，這些構成 c 樣式的方法的例外處理\)。  
  
## 語法  
  
```cpp  
HRESULT get_hasSetJump(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式中包含`setjmp`指令。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)