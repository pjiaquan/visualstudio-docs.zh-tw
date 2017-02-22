---
title: "IDiaSymbol::get_lexicalParentId | Microsoft Docs"
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
  - "IDiaSymbol::get_lexicalParentId 方法"
ms.assetid: 6c0c2874-cc47-4e4f-ad9c-02a18a108d9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_lexicalParentId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取識別語彙的父項的符號。  
  
## 語法  
  
```cpp#  
HRESULT get_lexicalParentId (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回語彙的父代 ID 的符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 識別項是唯一的值，由 DIA SDK 將標示為唯一的所有符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)