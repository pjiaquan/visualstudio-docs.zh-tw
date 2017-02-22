---
title: "IDiaSectionContrib::get_code16bit | Microsoft Docs"
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
  - "IDiaSectionContrib::get_code16bit 方法"
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_code16bit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否區段包含 16 位元的程式碼。  
  
## 語法  
  
```cpp#  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`一節中的程式碼是否為 16 位元。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法只會表示，是否程式碼是 16 位元的位置。  如果程式碼不是 16 位元，則可能是任何動作，例如 32 位元或 64 位元的程式碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)