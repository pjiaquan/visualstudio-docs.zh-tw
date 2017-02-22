---
title: "IDiaSectionContrib::get_relocationsCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_relocationsCrc 方法"
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_relocationsCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取 \[循環冗餘檢查 \(CRC\) 區段的重新配置資訊。  
  
## 語法  
  
```cpp#  
HRESULT get_relocationsCrc (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的 CRC 時的區段的重新配置資訊。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)