---
title: "IDiaEnumInjectedSources::get_Count | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::get_Count 方法"
ms.assetid: 659c415b-9f7b-470d-90e2-b4c0087f8dd3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取插入來源的數目。  
  
## 語法  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[\] out傳回插入來源的數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)