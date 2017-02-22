---
title: "IDiaSectionContrib::get_comdat | Microsoft Docs"
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
  - "IDiaSectionContrib::get_comdat 方法"
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_comdat
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指示區段是否為衝突的記錄。  
  
## 語法  
  
```cpp#  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果區段是一種 COMDAT 筆記錄。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 衝突記錄是讓封裝函式的連結器的 \[看得見的通用物件檔案格式 \(COFF\) 記錄。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)