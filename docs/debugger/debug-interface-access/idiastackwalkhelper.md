---
title: "IDiaStackWalkHelper | Microsoft Docs"
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
  - "IDiaStackWalkHelper2 介面"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

幫助您查核堆疊使用程式的偵錯資料庫 \(.pdb\) 檔案。  
  
## 語法  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## 方法 VTable 順序  
 下表顯示的方法`IDiaStackWalkHelper`：  
  
|方法|描述|  
|--------|--------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|擷取暫存器的值。|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|設定暫存器的值。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|在記憶體中的可執行檔映像可讀取資料的區塊。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|搜尋指定的堆疊框架的最接近的函式傳回的位址。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|搜尋指定的堆疊框架的回覆地址在 100%或接近指定的堆疊位址。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|擷取包含指定的虛擬位址的堆疊框架。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|擷取包含指定的虛擬位址的符號。 **Note:**  符號必須要有類型`SymTagFunctionType` \(介於[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別\)。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|傳回指定的虛擬位址相關聯的 PDATA 資料區塊。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|擷取指定的虛擬位址某處的可執行檔的記憶體空間中的可執行檔的起始虛擬位址。|  
  
## 備註  
 這個介面會呼叫 DIA 程式碼，以取得資訊的可執行檔，在程式執行期間建構的堆疊框架的清單。  
  
## 呼叫者的備忘稿  
 用戶端應用程式會實作這個介面以支援在程式執行期間查核堆疊。  這個介面的執行個體傳遞至[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)或[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)方法。  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)