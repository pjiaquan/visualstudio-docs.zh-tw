---
title: "IDiaEnumSegments::get_Count | Microsoft Docs"
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
  - "IDiaEnumSegments::get_Count 方法"
ms.assetid: c62a0fda-17b8-4cf6-b321-6014ce581096
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的線段數目。  
  
## 語法  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[retval\] out傳回的線段數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)