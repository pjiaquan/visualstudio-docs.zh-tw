---
title: "IDiaEnumSourceFiles::Clone | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Clone 方法"
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立列舉值，包含目前的列舉值的列舉型別狀態。  
  
## 語法  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSourceFiles** ppenum  
);  
```  
  
#### 參數  
 ppenum  
 \[\] out傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)物件，包含列舉值已經存在。  來源檔案不被重複的列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)