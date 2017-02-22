---
title: "IDiaTable::get_name | Microsoft Docs"
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
  - "IDiaTable::get_name 方法"
ms.assetid: f6e9cd07-63cd-48a6-9835-e69c2d0859c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::get_name
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取資料表的名稱。  
  
## 語法  
  
```cpp#  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回資料表的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)