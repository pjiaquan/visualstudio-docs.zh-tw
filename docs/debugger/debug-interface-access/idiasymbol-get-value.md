---
title: "IDiaSymbol::get_value | Microsoft Docs"
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
  - "IDiaSymbol::get_value 方法"
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_value
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取常數的值。  
  
## 語法  
  
```cpp#  
HRESULT get_value (   
   VARIANT* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 輸入 \[、 輸出\]A `VARIANT`會被填入了常數的值的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 必須先初始化所提供的變體，它會傳遞至這個方法。  如需詳細資訊，請參閱範例。  
  
## 範例  
  
```cpp#  
void ProcessValue(IDiaSymbol *pSymbol)  
{  
    VARIANT value;  
    value.vt = VT_EMPTY;    // Initialize variant for use.  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value.  
    }  
}  
  
//----------------------------------------------------  
// Alternate approach  
void ProcessValue2(IDiaSymbol *pSymbol)  
{  
    CComVariant value;  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value  
    }  
}  
```  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)