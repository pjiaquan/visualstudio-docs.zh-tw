---
title: "IDiaSymbol::get_hasSecurityChecks | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSecurityChecks 方法"
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasSecurityChecks
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定是否已編譯的編譯或函式的緩衝區滿溢的安全性檢查 \(例如， [\/GS \(緩衝區安全性檢查\)](/visual-cpp/build/reference/gs-buffer-security-check)編譯器參數\)。  
  
## 語法  
  
```cpp#  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式有任何安全性檢查。 否則，會傳回`FALSE`。  
  
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
 [\/GS \(緩衝區安全性檢查\)](/visual-cpp/build/reference/gs-buffer-security-check)