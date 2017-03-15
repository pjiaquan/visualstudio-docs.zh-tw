---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::pdataByVA 方法"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回虛擬地址相關聯的 PDATA 資料區塊。  
  
## 語法  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### 參數  
 `va`  
 \[in\]指定要取得之資料的虛擬位址。  
  
 `cbData`  
 \[in\]以位元組為單位，以取得的資料大小。  
  
 `pcbData`  
 \[\] out傳回資料的實際大小，以位元組為單位取得。  
  
 `pbData`  
 輸入 \[、 輸出\]這種緩衝區會填入這些要求的資料。  不可為 `NULL`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有指定的位址沒有 PDATA。  否則，會傳回錯誤碼。  
  
## 備註  
 PDATA \(名為".pdata 」 一節\) 的編譯包含函式所處理的例外狀況的相關資訊。  
  
 呼叫端知道所要讓呼叫者必須向多少資料會出現不需要傳回的資料量。  因此，是可以接受對這個方法來傳回錯誤訊息，如果實作的`pbData`參數是`NULL`。  
  
## 請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)