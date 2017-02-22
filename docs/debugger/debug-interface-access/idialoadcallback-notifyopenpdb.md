---
title: "IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenPDB 方法"
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

候選.pdb 檔案開啟時呼叫。  
  
## 語法  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### 參數  
 `pdbPath`  
 \[in\].Pdb 檔案的完整路徑。  
  
 `resultCode`  
 \[in\]指出是否成功的程式碼 \(`S_OK`\) 或套用至這個檔案載入失敗。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回的程式碼通常會被忽略。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)