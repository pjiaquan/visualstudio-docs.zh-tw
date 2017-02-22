---
title: "維度 | Microsoft Docs"
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
  - "維度符號"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 維度
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每個 FORTRAN 陣列的維度，由`SymTagDimension`符號。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_lowerBound](../Topic/IDiaSymbol::get_lowerBound.md)|`IDiaSymbol*`|個 FORTRAN 陣列維度的下限。|  
|[IDiaSymbol::get\_lowerBoundId](../Topic/IDiaSymbol::get_lowerBoundId.md)|`DWORD`|下限符號的識別碼。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagDimension` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|個 FORTRAN 陣列維度的上限。|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|上限符號的識別碼。|  
  
## 請參閱  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)