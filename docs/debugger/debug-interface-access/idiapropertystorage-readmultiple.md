---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取指定從目前的屬性集合的內容。  
  
## 語法  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### 參數  
 `cpspec`  
 \[in\]Count 屬性中指定的`rgpspec`陣列。  如果是零，這個方法會傳回任何屬性，但會傳回`S_OK`為成功的程式碼。  
  
 `rgpspec`  
 \[in\]要讀取的屬性陣列。  屬性識別碼或在長條圖裡的名稱，則可以指定屬性。  您不需要指定陣列中的任何特定順序的屬性。  此陣列可以包含重複的屬性，使得在簡單屬性的傳回重複的屬性值。  非簡單屬性應該傳回嘗試開啟第二次拒絕存取。  陣列可以包含多種屬性識別碼和字串識別碼。  這個陣列至少必須有`cpspec`屬性值的數字。  
  
 `rgvar`  
 輸入 \[、 輸出\]陣列的`PROPVARIANT` \(在 Microsoft.VisualStudio.OLE.Interop 命名空間中\) 結構來填入每個屬性的值。  陣列必須至少為`cpspec`元素的大小。  呼叫端不需要初始化陣列中的值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果找不到一或多個屬性。  否則會傳回錯誤碼。  
  
## 備註  
 如果屬性已經找不到，對應的進入點，在`rgvar`陣列會包含`VARIANT`的型別`VT_EMPTY`。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)