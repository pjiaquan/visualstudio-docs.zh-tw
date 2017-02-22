---
title: "IDiaEnumSourceFiles::Item | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Item 方法"
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的索引的原始程式檔。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### 參數  
 Index \- 索引  
 \[in\]索引的[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)要擷取的物件。  索引是以介於 0 到`count`\-1，其中 `count`傳回的[IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md)方法。  
  
 sourceFile  
 \[\] out傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表您想要的原始程式檔。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)