---
title: "IDiaSymbol::get_hfaDouble | Microsoft Docs"
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
  - "IDiaSymbol::get_hfaDouble 方法"
ms.assetid: efc247b9-c16e-4fa3-89b0-901caf7b74c3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hfaDouble
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定使用者定義的型別 \(UDT\) 是否包含同質浮點彙總 \(HFA\) 資料的雙精度浮點型別。  
  
## 語法  
  
```cpp#  
HRESULT get_hfaDouble(   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果 UDT 包含 HFA 的資料型別雙精度浮點 ； 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia100.dll  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)