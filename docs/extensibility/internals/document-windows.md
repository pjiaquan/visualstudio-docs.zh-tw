---
title: "文件視窗 | Microsoft Docs"
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
  - "Visual Studio SDK 文件視窗"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 文件視窗
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中， *文件視窗* 是相關聯的多重文件介面 \(MDI\) 視窗框架的子視窗。 文件視窗通常用於顯示和修改原始程式碼或文字，但它們也可以裝載其他功能的類型。 文件視窗中︰  
  
-   可以組織在 MDI 父代中的另一個水平或垂直索引標籤群組中，以便可以同時檢視多個檔案。  
  
-   可停駐在 MDI 父代中的任何順序。  
  
-   可以是自由浮動。  
  
-   連結到其他 MDI 視窗的定位順序。  
  
 群組的命令，停駐和浮動位於文件視窗索引標籤的捷徑功能表。  
  
 如需在 Visual Studio 中的視窗行為的詳細資訊，請參閱 [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
## 文件視窗實作  
 文件視窗是由實作編輯器建立的。<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 介面會建立具現化編輯器的一部分的文件視窗。 如需詳細資訊，請參閱[在編輯器中的傳統介面](../../extensibility/legacy-interfaces-in-the-editor.md)。  
  
> [!NOTE]
>  若要提供向後和向前巡覽點，在視窗中的，實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 介面。 文字編輯器會使用文字標記來識別文件中的 \[瀏覽點。  
  
## 執行文件資料表  
 IDE 會使用執行中的文件表格 \(RDT\) 來追蹤每個文件視窗的狀態。 RDT 是透過哪份文件視窗會收到通知的事件，例如當關閉方案或檔案已經過編輯的機制。 如需詳細資訊，請參閱[執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
## 請參閱  
 [延遲的文件載入](../../extensibility/internals/delayed-document-loading.md)