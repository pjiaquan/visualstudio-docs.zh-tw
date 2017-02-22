---
title: "持續性和執行文件資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "持續性，管理"
  - "IVsPersistHierarchyItem 介面實作"
  - "持續性的架構"
  - "執行文件中的表格 (RDT) 架構"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 持續性和執行文件資料表
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE，專案會完全負責管理其專案項目，在完成使用服務時，持續性 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 文件是在 Visual Studio 環境中的持續性的基本單位。 專案協調開啟、 儲存和重新命名的文件執行文件中的表格 \(RDT\)，會追蹤所有開啟的文件狀態的資源。  
  
## 管理持續性  
 專案控制環境的持續性服務，藉由實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 介面。 雖然環境絕對不會直接詢問要保存本身的文件時，它會要求儲存文件的主控專案 \(或階層\)。 這可讓專案，以將其專案項目資料儲存到本機檔案、 遠端檔案、 資料庫、 儲存機制或其他媒體。  
  
 全域環境維護 RDT。 環境會維護所有已開啟視窗的項目和文件 RDT，這樣就能讓他們在收到特殊的通知，例如關閉方案時。 RDT 此外，可讓追蹤其對應的節點中的環境 **方案總管\] 中**。 RDT 會維護每個開啟的、 永續性物件，包括專案檔和專案項目文件的一筆記錄。  
  
## 請參閱  
 [執行中的文件表格](../../extensibility/internals/running-document-table.md)   
 [選取項目和 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)