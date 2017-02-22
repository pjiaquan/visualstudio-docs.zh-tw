---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign 方法"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定影像的對齊方式。  
  
## 語法  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### 參數  
 NewVal  
 \[in\]新影像的對齊值可執行檔。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 \(載入可執行檔\) 的影像對齊至指定的記憶體範圍。  依目前的系統架構和編譯和連結的 \[時間\] 選項，可能會影響這種對齊。  對齊影像一定是位元組邊界上。  下列影像對齊有效值: 1、 2、 4、 8、 16、 32 及 64 位元組的界限。  
  
 可擷取目前的影像對齊方式，有一個呼叫[IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)方法。  
  
> [!NOTE]
>  影像已被載入時可以呼叫這個方法。  `put_imageAlign`方法通常用時，已經移動或變更影像需要新的對齊方式。  
  
## 請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)