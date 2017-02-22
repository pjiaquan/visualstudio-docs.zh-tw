---
title: "IDiaInjectedSource::get_virtualFilename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_virtualFilename 方法"
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_virtualFilename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定給非檔案來源的程式碼路徑。 也就是插入的程式碼。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualFilename (   
   BSTR* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回指定給插入的非檔案來源的程式碼的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)