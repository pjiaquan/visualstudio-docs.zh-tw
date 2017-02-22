---
title: "IDiaSymbol::get_rank | Microsoft Docs"
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
  - "IDiaSymbol::get_rank 方法"
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取 FORTRAN 多維陣列的陣序規範 \(維度數目\)。  
  
## 語法  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回在 FORTRAN 多維陣列的維度數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 陣序規範是指在陣列宣告為一個陣列中的維度數目`myarray[1,2,3]`。  這個範例包含排名為 3 且為 3 的維度。  陣序規範不適用於 C\+\+ 中為每個維度使用的陣列的陣列概念 \(也就是`myarray[1][2][3]`\)。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)