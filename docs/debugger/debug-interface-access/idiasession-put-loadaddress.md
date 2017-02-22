---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
  - "IDiaSession::put_loadAddress 方法"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將相對應的可執行檔的載入位址設定符號這個符號存放區中。  
  
## 語法  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### 參數  
 `NewVal`  
 \[in\]載入可執行檔的位址。  
  
## 備註  
 符號的虛擬位址 \(VA\) 屬性，會使用這個方法的值計算出來的。  除非這個屬性將設為非零，不被計算虛擬位址。  
  
> [!NOTE]
>  您必須呼叫這個方法，當您在[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，並開始使用物件，如果您需要在符號上使用任何虛擬屬性之前。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)