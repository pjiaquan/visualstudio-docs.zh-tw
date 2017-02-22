---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program 方法"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取程式字串，用來計算目前的函式呼叫之前設定的暫存器。  
  
## 語法  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回程式的字串。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 該程式字串是一連串的巨集，才能建立初構會被解譯。  例如，典型的堆疊框架可能會使用程式字串`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`。  格式是反向波蘭文表示法中，運算子遵照運算元的位置。  `T0`表示在堆疊上的暫存變數。  本範例會執行下列步驟：  
  
1.  移動暫存器的內容`ebp`到`T0`。  
  
2.  新增`4`中的`T0`產生地址，該地址，取得值，並將值儲存在暫存器`eip`。  
  
3.  取得值的地址儲存在`T0` ，並將該值儲存在暫存器中`ebp`。  
  
4.  新增`8`中的`T0` ，並將該值儲存在暫存器中`esp`。  
  
 請注意程式字串特定 CPU，並設定成 \[由目前的堆疊框架的函式的呼叫慣例。  
  
## 請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)