---
title: "原始檔控制外掛程式 API 版本 1.3 新功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式的新 API v1.3"
  - "什麼是新 [Visual Studio SDK]，原始檔控制外掛程式"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 原始檔控制外掛程式 API 版本 1.3 新功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

原始檔控制外掛程式 API 1.3 版引入了下列的新功能，以提供更進階的控制項。  
  
## 變更  
 下列函式會新增至原始檔控制外掛程式 API 1.3 版：  
  
|Function|概觀|  
|--------------|--------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|可讓報告的另一項功能位元|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|可以讓檢查中版本控制資料庫比在本機磁碟上有較新版本的檔案|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允許指定的檔案名稱變更 \(重新命名、 加入項目和刪除\) 的狀態檢查|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|可以讓目錄和檔案的版本控制資料庫中的檢查結果|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|將指定的檔案清單從版本控制資料庫加入至目前的專案|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行無訊息"Get"指定的檔案 \(無使用者介面會顯示\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允許存取特定的使用者選項|  
  
## 請參閱  
 [使用者入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)