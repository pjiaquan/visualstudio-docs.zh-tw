---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取相對應的字串名稱指定的屬性識別項。  
  
## 語法  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### 參數  
 `cpropid`  
 \[in\]數字中的屬性 id 的`rgpropid`。  
  
 `rgpropid`  
 \[in\]要取得名稱的屬性 id 的陣列 \(`PROPID`與 WTypes.h 所述`ULONG`\)。  
  
 `rglpwstrName`  
 輸入 \[、 輸出\]指定的屬性 id 的屬性名稱的陣列。  陣列必須預先配置來保留要求的屬性名稱的數目，且必須能夠容納至少`cpropid``BSTR`的字串。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 備註  
 必須釋放傳回的屬性名稱 \(藉由呼叫`SysFreeString`函式\) 在不再需要時。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)