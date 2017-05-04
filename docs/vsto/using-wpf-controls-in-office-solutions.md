---
title: "在 Office 方案中使用 WPF 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WPF [Visual Studio 中的 Office 程式開發]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 在 Office 方案中使用 WPF 控制項
  雖然 Visual Studio 中使用 Office 開發工具所建立的解決方案設計成直接使用 Windows Form 控制項，您也可以在解決方案中使用 WPF 控制項。  Windows Presentation Foundation \(WPF\) 是 Windows Form 設計使用者介面的替代方式。  WPF 使用稱為 Extensible Application Markup Language \(XAML\) 的標記語言，提供納入 UI、媒體和文件新技術。  如需詳細資訊，請參閱 [Visual Studio 2015 中的 WPF 簡介](http://msdn.microsoft.com/library/582a314e-e23d-4144-b45b-acbbd5579252)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 任何可在 Office 方案中裝載 Windows Form 控制項的 UI 元素，也可以裝載 WPF 控制項。  它們包括下列元素：  
  
-   文件層級自訂的文件和工作表。  
  
-   文件層級自訂的執行窗格。  
  
-   VSTO 增益集的自訂工作窗格。  
  
-   Outlook VSTO 增益集的表單區域。  
  
## 在設計階段將 WPF 控制項加入 Office 專案中  
 您無法在 Office 方案的 UI 元素中直接加入 WPF 控制項。  而是要在專案中加入 \[使用者控制項 \(WPF\)\] 項目，然後用為 WPF 控制項的設計介面。  然後，在專案的 UI 元素中加入 WPF 使用者控制項。  
  
#### 在執行窗格、自訂工作窗格或表單區域加入 WPF 控制項  
  
1.  開啟要加入自訂工作窗格、執行窗格或表單區域的專案。  
  
2.  在專案中加入 \[使用者控制項 \(WPF\)\] 項目。  
  
3.  從 \[工具箱\] 將 WPF 控制項加入 WPF 使用者控制項的設計介面。  
  
     當 WPF 使用者控制項設計工具開啟時，\[工具箱\] 預設會只包含 WPF 控制項。  
  
4.  建置專案。  
  
5.  在專案中加入執行窗格、表單區域或自訂工作窗格：  
  
    -   對於表單區域，請在專案中加入 \[Outlook 表單區域\] 項目。  如需詳細資訊，請參閱[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
    -   對於執行窗格，請在專案中加入 \[執行窗格控制項\] 或 \[使用者控制項\] 項目。  如需詳細資訊，請參閱[如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)和[如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
    -   對於自訂工作窗格，請在專案中加入 \[使用者控制項\] 項目。  如需詳細資訊，請參閱[如何：在應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
6.  從 \[工具箱\] 的*專案名稱* \[WPF 使用者控制項\] 索引標籤中，將 WPF 使用者控制項拖曳至執行窗格、表單區域或自訂工作窗格的設計工具。  
  
     Visual Studio 會自動建立在 UI 元素上裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
7.  重建專案。  
  
#### 在文件層級專案的文件或工作表中加入 WPF 控制項  
  
1.  開啟 Word 或 Excel 的文件層級專案。  
  
2.  在專案中加入 \[使用者控制項 \(WPF\)\] 項目。  
  
3.  從 \[工具箱\] 將 WPF 控制項加入 WPF 使用者控制項的設計介面。  
  
4.  建置專案。  
  
5.  在專案中加入 \[使用者控制項\] 項目 \(也就是 Windows Form 使用者控制項\)。  
  
6.  開啟 Windows Form 使用者控制項的設計工具。  
  
7.  從 \[工具箱\] 的*專案名稱* \[WPF 使用者控制項\] 索引標籤中，將 WPF 使用者控制項拖曳至設計工具。  
  
     Visual Studio 會自動建立在 Windows Form 使用者控制項中裝載 WPF 使用者控制項的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
8.  撰寫程式碼，以程式設計方式將 Windows Form 使用者控制項加入文件或活頁簿。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
    > [!NOTE]  
    >  您無法將 Windows Form 使用者控制項拖曳至設計工具的文件或工作表。  
  
9. 重建專案。  
  
## 使用 ElementHost 類別裝載 WPF 控制項  
 Visual Studio 提供的功能，會協助您在 Office 方案中使用 Windows Form 控制項，但對 WPF 控制項則不提供類似的功能。  例如，您可以在設計階段從 \[工具箱\] 拖曳控制項，或在執行階段使用 helper 方法，將 Windows Form 控制項加入文件和工作表。  不過，WPF 控制項無法使用這些工具。  
  
 WPF 控制項將 <xref:System.Windows.Forms.Integration.ElementHost> 類別用做 Windows Form 控制項或表單和 WPF 控制項之間的整合層。  當您在設計階段將 WPF 控制項加入解決方案時，Visual Studio 會為您自動產生 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
## WPF 資源  
 如需在 Windows Form 控制項和表單上裝載 WPF 控制項的架構和設計問題的詳細資訊，請參閱下列主題：  
  
-   [Windows Form 和 WPF 互通性輸入架構](http://msdn.microsoft.com/library/0eb6f137-f088-4c5e-9e37-f96afd28f235)  
  
-   [Windows Form 和 WPF 屬性對應](http://msdn.microsoft.com/library/999d8298-9c04-467d-a453-86e41002057d)  
  
-   [WPF 和 Windows Form 互通](http://msdn.microsoft.com/library/9e8aa6b6-112c-4579-98d1-c974917df499)  
  
-   [Windows Form 控制項和對等 WPF 控制項](http://msdn.microsoft.com/library/8a157e6b-8054-46db-a5cf-a78966acc7a1)  
  
 如需在設計階段於 Visual Studio 的 Windows Form 控制項和表單中加入 WPF 控制項的詳細資訊，請參閱下列主題：  
  
-   [逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](http://msdn.microsoft.com/library/2e92d8e8-f0e4-4df7-9f07-2acf35cd798c)  
  
-   [逐步解說：在設計階段排列 Windows Form 的 WPF 內容](http://msdn.microsoft.com/library/5efb1c53-1484-43d6-aa8a-f4861b99bb8a)  
  
-   [逐步解說：設定 WPF 內容的樣式](http://msdn.microsoft.com/library/e574aac7-7ea4-4cdb-8034-bab541f000df)  
  
## 請參閱  
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：在應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  