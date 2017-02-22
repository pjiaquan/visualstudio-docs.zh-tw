---
title: "SccQueryChanges 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges 函式"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccQueryChanges 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會列舉指定的檔案，並提供每個檔案透過回呼函式的名稱變更的相關資訊清單。  
  
## 語法  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 nFiles  
 \[\] in中的檔案數目 `lpFileNames` 陣列。  
  
 lpFileNames  
 \[\] in要取得相關資訊的檔案名稱的陣列。  
  
 pfnCallback  
 \[\] in若要在清單中每個檔案名稱呼叫的回呼函式 \(請參閱 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 如需詳細資訊\)。  
  
 pvCallerData  
 \[\] in將會原封不動地傳遞至回呼函式的值。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|查詢處理程序已順利完成。|  
|SCC\_E\_PROJNOTOPEN|不在原始檔控制開啟專案。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC\_E\_NONSPECIFICERROR|發生未指定或一般錯誤。|  
  
## 備註  
 變更要查詢的命名空間: 具體而言，重新命名、 新增和移除檔案。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [錯誤代碼](../extensibility/error-codes.md)