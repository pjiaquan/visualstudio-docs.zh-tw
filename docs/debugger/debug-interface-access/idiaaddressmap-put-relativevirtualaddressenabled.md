---
title: "IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_relativeVirtualAddressEnabled 方法"
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

允許用戶端啟用或停用的計算和相對虛擬位址 \(RVA\) 的使用。  
  
## 語法  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### 參數  
 NewVal  
 \[in\]設定成`TRUE`若要啟用，或`FALSE`來停用。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 可以擷取描述 DIA 介面，以及如何在可執行檔映像基底，相對的偵錯物件的位址為相對虛擬位址。  
  
 PDB 檔案從一開始載入區段時，會啟用之 Rva 使用。  若要取得之 Rva 使用的目前狀態，呼叫[IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法。  
  
 `put_relativeVirtualAddress`必須呼叫方法，以便成功呼叫之後的 Rva [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)方法已建立新的映像標頭。  
  
## 請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)