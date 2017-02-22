---
title: "IDiaSectionContrib::get_informational | Microsoft Docs"
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
  - "IDiaSectionContrib::get_informational 方法"
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_informational
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否一個區段包含註解或類似的資訊。  
  
## 語法  
  
```cpp#  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果區段包含註解或其他資訊。 否則會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 通常 \[.directive\] 區段中包含的資訊。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)