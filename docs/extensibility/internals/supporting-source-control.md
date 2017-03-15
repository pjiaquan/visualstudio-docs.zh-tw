---
title: "支援的原始檔控制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制 [Visual Studio SDK] 支援"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 支援的原始檔控制
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援的檔案簽出、 簽入和其他編輯器或專案的原始檔控制作業。  原始檔控制用戶端， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的設計能與原始檔控制套件，例如[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]，提供保存、 版本控制和控制設施給動態定義的一組檔案。  
  
## 在本節中  
 [原始檔控制套件的模型](../../extensibility/internals/model-for-source-control-packages.md)  
 描述專案型別必須實作的介面來支援原始檔控制。  
  
 [設計決策](../../extensibility/internals/source-control-design-decisions.md)  
 提供的問題的答案變更實作專案類型的方式。  
  
 [設定詳細資料](../../extensibility/internals/source-control-configuration-details.md)  
 說明如何支援原始檔控制變更的專案型別實作。  
  
 [專案和編輯器的其他指導方針](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 討論專案類型和編輯器的最佳作法。  
  
 [執行階段詳細資料](../../extensibility/internals/source-control-runtime-details.md)  
 說明如何註冊專案，當使用者將其加入至原始檔控制系統。  
  
## 參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 指示檔案是在記憶體中變更或儲存的原始檔控制套件的環境。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 可讓專案以及註冊與原始檔控制的方式，並取得原始檔控制狀態的相關資訊的階層架構。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 在專案檔和專案項目提供原始檔控制的專案系統中實作。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 由專案中使用查詢來新增、 移除或重新命名檔案或目錄方案中的權限的環境。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 告知用戶端的專案檔案或目錄所做的變更。  
  
## 相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 概述專案作為基本的建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  提供說明如何專案控制建置和編譯程式碼的其他主題的連結。