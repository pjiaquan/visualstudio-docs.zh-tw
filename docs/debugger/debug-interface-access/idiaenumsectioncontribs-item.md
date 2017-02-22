---
title: "IDiaEnumSectionContribs::Item | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Item 方法"
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的索引的區段佔的比重。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### 參數  
 Index \- 索引  
 \[in\]索引的[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)要擷取的物件。  索引是以介於 0 到`count`\-1，其中`count`傳回的[IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)方法。  
  
 區段  
 \[\] out傳回[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件，代表您想要的一節所佔的比重。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)