---
title: "IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs"
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
  - "IDiaSymbol::get_optimizedCodeDebugInfo 方法"
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_optimizedCodeDebugInfo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取旗標 \(指出函式是否包含偵錯工具將最佳化程式碼是特定的資訊。  
  
## 語法  
  
```cpp  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[out\] ，如果最佳化函式或標籤包含偵錯資訊，則傳回 `TRUE` ;否則，會傳回 `FALSE`。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
> [!NOTE]
>  `S_FALSE` 的傳回值表示屬性的符號無法使用。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標題:|dia2.h|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)