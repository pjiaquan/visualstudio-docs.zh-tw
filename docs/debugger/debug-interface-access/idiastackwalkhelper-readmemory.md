---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory 方法"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在記憶體中的可執行檔映像可讀取資料的區塊。  
  
## 語法  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### 參數  
 `type`  
 \[in\]介於[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)指定的記憶體讀取型別列舉型別。  
  
 va  
 \[in\]要開始讀取映像中的虛擬位址。  
  
 `cbData`  
 \[in\]資料緩衝區的大小以位元組為單位。  
  
 `pcbData`  
 \[\] out傳回實際讀取的位元組數目。  如果`pbData`是`NULL`，那麼這就是可以使用資料的位元組總數。  
  
 `pbData`  
 輸入 \[、 輸出\]這種緩衝區會填入這些讀取的記憶體。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)