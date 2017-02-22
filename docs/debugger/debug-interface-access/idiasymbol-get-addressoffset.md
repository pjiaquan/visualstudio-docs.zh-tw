---
title: "IDiaSymbol::get_addressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_addressOffset 方法"
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取位移的組件的地址的位置。  何時使用[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 \[ `LocIsStatic`。  
  
## 語法  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的地址位置位移的部份。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 備註  
 對於位於外部的 DLL 中的靜態成員，這個方法所傳回的位移可能為 0，因為這個方法會依賴取得成員的虛擬位址。  是有效的虛擬位址才[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)中的方法[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面呼叫具有非零值的參數，指定 DLL 的載入位址。  
  
 若要取得的地址\] 區段部份，呼叫[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)方法。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)