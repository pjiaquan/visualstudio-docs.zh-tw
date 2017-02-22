---
title: "IDiaSymbol::get_virtualTableShapeId | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualTableShapeId 方法"
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualTableShapeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取虛擬資料表圖形符號識別項的符號。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualTableShapeId (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回虛擬資料表的符號 ID 的符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 備註  
 識別項是唯一的值，由 DIA SDK 將標示為唯一的所有符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)