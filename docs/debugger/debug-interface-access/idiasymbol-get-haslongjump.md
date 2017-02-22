---
title: "IDiaSymbol::get_hasLongJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasLongJump 方法"
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的函式是否包含一種使用其中一個旗標[longjmp](/visual-cpp/c-runtime-library/reference/longjmp)命令 \(與放大的成對[setjmp](/visual-cpp/c-runtime-library/reference/setjmp)命令，這些構成 c 樣式的方法的例外處理\)。  
  
## 語法  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式中包含`longjmp`指令。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)