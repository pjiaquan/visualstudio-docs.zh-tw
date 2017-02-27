---
title: "SccPopulateDirList 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList 函式"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# SccPopulateDirList 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會判斷哪些目錄以及 \(選擇性檔案\) 會儲存在原始檔控制，提供要檢查的目錄清單。  
  
## 語法  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 nDirs  
 \[\] in目錄路徑中的數字 `lpDirPaths` 陣列。  
  
 lpDirPaths  
 \[\] in若要檢查的目錄路徑的陣列。  
  
 pfnPopulate  
 \[\] in回呼函式呼叫的每個目錄路徑和 \(選擇性\) 在檔名 `lpDirPaths` \(請參閱 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 如需詳細資訊\)。  
  
 pvCallerData  
 \[\] in要傳遞至回呼函式不變的值。  
  
 Stored  
 \[\] in這些值會控制目錄的處理方式的組合 \(請參閱 「 PopulateDirList 旗標 」 一節 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md) 提供可能的值\)。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|順利完成作業。|  
|SCC\_E\_UNKNOWNERROR|發生錯誤。|  
  
## 備註  
 只有這些目錄和 \(選擇性\) 實際上是在原始檔控制儲存機制的檔案名稱會傳遞至回呼函式。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [錯誤代碼](../extensibility/error-codes.md)