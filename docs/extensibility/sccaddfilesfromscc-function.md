---
title: "SccAddFilesFromSCC 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC 函式"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFilesFromSCC 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式將從原始檔控制中的檔案清單加入至目前開啟的專案。  
  
## 語法  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpUser  
 \[in、 out\]\(最多 SCC\_USER\_SIZE，包括 null 結束字元\) 使用者名稱。  
  
 lpAuxProjPath  
 \[in、 out\]識別專案的輔助字串 \(最多 `SCC_PRJPATH_`大小，包括 null 結束字元\)。  
  
 cFiles  
 \[\] in所指定的檔案數目 `lpFilePaths`。  
  
 lpFilePaths  
 \[in、 out\]要加入至目前專案的檔案名稱陣列。  
  
 lpDestination  
 \[\] in目的地路徑寫入檔案的位置。  
  
 lpComment  
 \[\] in要套用至每個檔案要加入註解。  
  
 pbResults  
 \[in、 out\]會設定為表示成功 \(非零或 TRUE\) 或失敗的旗標的陣列 \(零或 FALSE\) 的每個檔案 \(陣列的大小必須至少 `cFiles` 長\)。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_E\_PROJNOTOPEN|無法開啟專案。|  
|SCC\_E\_OPNOTPERFORMED|連接不是為了與所指定相同的專案 `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|使用者無法更新資料庫的權限。|  
|SCC\_E\_NONSPECIFICERROR|未知的錯誤。|  
|SCC\_I\_RELOADFILE|需要重新載入檔案或專案。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)