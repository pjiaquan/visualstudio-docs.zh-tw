---
title: "檔案狀態的程式碼列舉值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "具名的常數，SccStatus 列舉值"
  - "原始檔控制外掛程式，檔案狀態列舉"
  - "SccStatus 列舉值"
  - "檔案狀態的程式碼列舉值"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 檔案狀態的程式碼列舉值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`SccStatus` 列舉值包含具名常數的值在原始檔控制系統中指定檔案的狀態。 這個列舉型別由 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 和 `POPLISTFUNC` 回呼函式 \(請參閱 [POPLISTFUNC](../extensibility/poplistfunc.md) 如需詳細資訊\)。  
  
## 語法  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## 成員  
 SCC\_STATUS\_INVALID  
 無法取得狀態。請勿依賴它。  
  
 SCC\_STATUS\_NOTCONTROLLED  
 檔案不是原始檔控制下。  
  
 SCC\_STATUS\_CONTROLLED  
 檔案是在 \[原始檔控制之下。  
  
 SCC\_STATUS\_CHECKEDOUT  
 簽出目前的使用者在本機磁碟上。  
  
 SCC\_STATUS\_OUTOTHER  
 檔案是由其他使用者簽出。  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 檔案是以獨佔方式簽出。  
  
 SCC\_STATUS\_OUTMULTIPLE  
 檔案是由多個使用者簽出。  
  
 SCC\_STATUS\_OUTOFDATE  
 檔案不是最新的。  
  
 SCC\_STATUS\_DELETED  
 已從專案刪除檔案。  
  
 SCC\_STATUS\_LOCKED  
 鎖定檔案;不允許更多的版本。  
  
 SCC\_STATUS\_MERGED  
 檔案已合併，但尚未固定\/驗證。  
  
 SCC\_STATUS\_SHARED  
 專案之間共用檔案。  
  
 SCC\_STATUS\_PINNED  
 明確的版本被共用檔案。  
  
 SCC\_STATUS\_MODIFIED  
 檔案已修改\/中斷\/違反了。  
  
 SCC\_STATUS\_OUTBYUSER  
 檔案是由目前使用者簽出。  
  
 SCC\_STATUS\_NOMERGE  
 檔案永遠不會與合併，並不需要儲存 GET 之前。  
  
 SCC\_STATUS\_RESERVED\_1  
 保留供內部使用。  
  
 SCC\_STATUS\_RESERVED\_2  
 保留供內部使用。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)