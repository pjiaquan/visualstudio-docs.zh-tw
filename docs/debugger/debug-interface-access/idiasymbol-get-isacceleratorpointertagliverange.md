---
title: "IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs"
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
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isAcceleratorPointerTagLiveRange
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的旗標符號是否對應至指標變數標記元件的定義 *範圍* 符號可為C\+\+. \+\+ AMP快速編譯的程式碼。  定義範圍符號是變數的位置位址範圍的。  
  
## 語法  
  
```cpp  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### 參數  
 `pFlag`  
 \[out\] 表示 `BOOL` 指標符號是否對應於定義範圍符號。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)