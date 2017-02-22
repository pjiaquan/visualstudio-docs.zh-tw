---
title: "IDiaAddressMap::get_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::get_imageAlign 方法"
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取目前的影像對齊方式。  
  
## 語法  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回可執行檔映像的對齊值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 影像會如何載入和建立映像已根據特定的記憶體界限對齊。  對齊方式通常是 1、 2、 4、 8、 16、 32 或 64 位元組的界限上。  可以設定影像的對齊方式，有一個呼叫[IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)方法。  
  
## 請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)