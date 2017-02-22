---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt 方法"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取指定的可執行檔從指定的位移處開始的位元組數。  
  
## 語法  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### 參數  
 fileOffset  
 \[in\]若要開始讀取的可執行檔中的位移。  
  
 cbData  
 \[in\]若要讀取的位元組數目。  
  
 pcbData  
 \[\] out傳回讀取的位元組數目。  
  
 資料\]  
 輸入 \[、 輸出\]會被填入從檔案讀取的位元組陣列。  
  
## 備註  
 這個方法會呼叫 DIA 支援程式碼中使用絕對檔案位移的可執行檔載入資料的位元組。  呼叫這個方法支援的[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## 請參閱  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)