---
title: "IDiaPropertyStorage::Enum | Microsoft Docs"
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
  - "IDiaPropertyStorage::Enum"
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

取得這個集合中屬性的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### 參數  
 `ppenum`  
 \[\] out傳回`IEnumSTATPROPSTG`物件 \(在 Microsoft.VisualStudio.OLE.Interop 命名空間中\)，表示屬性的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)