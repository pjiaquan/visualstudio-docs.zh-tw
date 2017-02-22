---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum 方法"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的加總檢查碼位元組。  
  
## 語法  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 參數  
 `cbData`  
 \[in\]資料緩衝區的大小，以位元組為單位。  
  
 `pcbData`  
 \[\] out傳回總和檢查碼的位元組數目。  這個參數不可以是 `NULL`。  
  
 `data`  
 輸入 \[、 輸出\]填滿的加總檢查碼位元組的緩衝區。  如果這個參數為`NULL`，然後`pcbData`傳回所需的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要判斷用來產生加總檢查碼位元組的加總檢查碼演算法的型別，呼叫[IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)方法。  
  
 通常，從原始程式檔的映像來產生加總檢查碼，因此原始程式檔中的變更會反映在加總檢查碼位元組中的變更。  如果不相符的總和檢查碼位元組總和檢查碼已載入的映像的檔案，請從產生的檔案應該被視為損毀，或竄改。  
  
 典型的加總檢查碼不會超過 32 個位元組的大小，但請不要假設這是最大大小的總和檢查碼。  設定`data`參數，以`NULL`以取得擷取的加總檢查碼所需的位元組數目。  然後配置適當大小的緩衝區，並呼叫這個方法一次多具有新的緩衝區。  
  
## 請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)