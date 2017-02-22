---
title: "IDiaSymbol::get_objectFileName | Microsoft Docs"
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
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_objectFileName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取物件的檔案名稱。  
  
## 語法  
  
```cpp  
HRESULT get_objectFilename(   
   BSTR *pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 保存物件檔案名稱變更為 `BSTR` 的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)