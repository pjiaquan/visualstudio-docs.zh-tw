---
title: "符號和符號標記 | Microsoft Docs"
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
  - "符號 [DIA SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 符號和符號標記
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

已編譯的程式有關的偵錯資訊存入程式資料庫 \(.pdb\) 檔案中，為可使用偵錯介面存取 \(DIA\) SDK Api 的符號。  所有的符號已經[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)和[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)屬性。  `symTag`屬性指示符號的類型，所定義的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  `symIndexId`屬性是`DWORD` ，其中包含的是符號的每個執行個體的唯一識別項的值。  
  
 符號也會有屬性，可以用指定的其他資訊的符號，以及其他的符號參考最常[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)或[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)。  當您查詢中包含參考的屬性時，做為傳回的參考[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。  這類屬性會永遠搭配另一個屬性以相同的名稱，但 suffixed"Id"，比方說， [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)和[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)。  在資料表[符號位置](../../debugger/debug-interface-access/symbol-locations.md)， [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)，以及[符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)概述每個不同的符號的內容。  檔案資訊清單或其他符號的參考，可能會有這些屬性。  因為`*Id`屬性只是數字的序數識別碼，其相關的屬性，它們將會略過進一步的討論區。  這些稱為只在所需的參數釐清的地方。  
  
 在嘗試存取的屬性，如果不會發生錯誤，而 \[符號\] 屬性已被指派一個值，該屬性的"get"方法傳回`S_OK`。  傳回值為`S_FALSE`表示的屬性不是適用於目前的符號。  
  
## 在本節中  
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)  
 描述不同的類型可以有一個符號的位置。  
  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 描述構成語彙的階層，例如檔案、 模組和函式的符號類型。  
  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 描述符號類型對應至不同的語言項目，例如類別、 陣列和函式傳回型別。  
  
## 請參閱  
 [偵錯 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/debug-interface-access-sdk.md)