---
title: "IDiaSectionContrib::get_notPaged | Microsoft Docs"
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
  - "IDiaSectionContrib::get_notPaged 方法"
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_notPaged
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否區段無法分頁記憶體用完。  
  
## 語法  
  
```cpp#  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[retval\] out傳回`TRUE`如果區段不能移出。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)