---
title: "IDiaInjectedSource::get_filename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_filename 方法"
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_filename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取來源的檔案名稱。  
  
## 語法  
  
```cpp#  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[\] out傳回來源的檔案名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)