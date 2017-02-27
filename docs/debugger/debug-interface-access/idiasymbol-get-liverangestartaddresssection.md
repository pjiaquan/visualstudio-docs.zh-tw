---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回本機符號是有效的範圍的起始位址中區段的一部份。  
  
## 語法  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### 參數  
 `section`  
 \[\] out傳回的區段部份開始的位址範圍。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  傳回的錯誤碼將表示符號沒有即時的範圍資訊。  
  
## 備註  
 構成方式的區段和位移的位址是範圍的符號是範圍的有效的開頭。  
  
 要位移的部分之地址，請使用[IDiaSymbol::get\_liveRangeStartAddressOffset](../Topic/IDiaSymbol::get_liveRangeStartAddressOffset.md)。  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia100.dll  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)