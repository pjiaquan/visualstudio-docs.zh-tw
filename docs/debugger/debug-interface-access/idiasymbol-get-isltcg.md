---
title: "IDiaSymbol::get_isLTCG | Microsoft Docs"
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
  - "IDiaSymbol::get_isLTCG 方法"
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isLTCG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的旗標是否[編譯模組](../../debugger/debug-interface-access/compiland.md)與連結器選項相連結[\/LTCG \(連結時間產生程式碼\)](/visual-cpp/build/reference/ltcg-link-time-code-generation)，這將會有助於在整個程式最佳化。  這個參數僅適用於 managed 程式碼。  
  
## 語法  
  
```cpp  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 pFlag  
 \[\] out傳回`TRUE`如果`compiland`連結以 \/LTCG 連結器參數。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)