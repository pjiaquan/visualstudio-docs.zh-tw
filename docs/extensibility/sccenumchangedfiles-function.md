---
title: "SccEnumChangedFiles 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "SccEnumChangedFiles 函式"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccEnumChangedFiles 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定本機檔案的清單，此函式，判斷哪些檔案是在原始程式碼控制資料庫中的對應版本不同。  
  
## 語法  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 cFiles  
 \[\] in檔案名稱中指定的數字 `lpFileNames` 陣列。 也會指定大小的 `plIsFileDifferent` 陣列。  
  
 lpFileNames  
 \[\] in若要檢查的本機檔案名稱的陣列。  
  
 plIsFileDifferent  
 \[in、 out\]值，指出每個檔案的不同狀態的陣列 \(陣列至少必須有 `cFiles` 項目\)。 檔案是不同的非零值表示。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|作業順利完成。|  
|SCC\_UNSPECIFIEDERROR|一般錯誤。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)