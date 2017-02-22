---
title: "IDiaStackWalkHelper::imageForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::imageForVA 方法"
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會傳回可執行檔映像的起始虛擬位址某處的可執行檔的記憶體空間中的記憶體中。  
  
## 語法  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### 參數  
 `vaContext`  
 \[in\]位於可執行檔的空間中的某處的虛擬位址。  
  
 `pvaImageStart`  
 \[\] out傳回的可執行檔映像的起始虛擬位址。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)