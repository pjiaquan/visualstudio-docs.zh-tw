---
title: "VSTO 增益集程式設計入門"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "增益集 [Visual Studio 中的 Office 程式開發], 使用者入門"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發], 使用者入門"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# VSTO 增益集程式設計入門
  您可以使用 VSTO 增益集來自動化 Microsoft Office 應用程式、擴充應用程式的功能，以及自訂應用程式的使用者介面 \(UI\)。  如需 VSTO 增益集與您可使用 Visual Studio 建立之其他類型 Office 方案相比較的相關資訊，請參閱 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## 建立 VSTO 增益集專案  
 使用 \[新增專案\] 對話方塊中的其中一個 VSTO 增益集專案範本，建立 VSTO 增益集專案。  這些範本包含必要的組件參考和專案檔。  Visual Studio 為 Office 中的大部分應用程式，提供 VSTO 增益集專案範本。  
  
 如需如何建立 VSTO 增益集專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  如需專案範本的詳細資訊，請參閱 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## 開發 VSTO 增益集專案  
 當您建立 VSTO 增益集專案時，Visual Studio 會自動建立 ThisAddIn.vb \(在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 中\) 或 ThisAddIn.cs \(在 C\# 中\) 程式碼檔。  這個檔案包含 `ThisAddIn` 類別，該類別會提供 VSTO 增益集的基礎。  載入或卸載 VSTO 增益集時，您可以使用這個類別的成員來執行程式碼，以存取主應用程式的物件模型及擴充應用程式的功能。  如需詳細資訊，請參閱 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
## 使用物件模型將應用程式自動化  
 Microsoft Office 應用程式的物件模型公開許多您可以在 VSTO 增益集中進行程式設計的類型。  您可以使用這些類型將應用程式自動化。  例如，您可以在 Outlook 中以程式設計的方式建立和傳送電子郵件訊息，也可以在 Word 中開啟文件和加入內容。  如需如何存取程式碼中主應用程式物件模型的詳細資訊，請參閱 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
 如需特定的 Microsoft Office 應用程式之物件模型的詳細資訊，請參閱下列主題：  
  
-   [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)  
  
-   [Word 物件模型概觀](../vsto/word-object-model-overview.md)  
  
-   [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath 方案](../vsto/infopath-solutions.md)  
  
-   [PowerPoint 方案](../vsto/powerpoint-solutions.md)  
  
-   [專案方案](../vsto/project-solutions.md)  
  
-   [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)  
  
## 自訂應用程式的使用者介面  
 使用 VSTO 增益集自訂主應用程式 UI 的方法有很多：  
  
-   對於 Excel 和 Word，您可以將 Managed 控制項加入文件。  如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
-   如果應用程式支援的話，您可以自訂功能區。  如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
-   如果應用程式支援的話，您可以建立自訂工作窗格。  如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
-   針對 Outlook，您可以建立自訂表單區域。  如需詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
-   對於所有 Microsoft Office 應用程式，您可以在 VSTO 增益集中顯示 Windows Form。  
  
 如需如何自訂 Microsoft Office 應用程式 UI 的詳細資訊，請參閱 [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## 後續步驟  
 若要了解如何建立 VSTO 增益集，請參閱下面的逐步解說：  
  
-   [逐步解說：建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [逐步解說：為您的 Outlook 建立第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [逐步解說：為您的 PowerPoint 建立第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [逐步解說：建立 Project 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [逐步解說：為您的 Word 建立第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 這些逐步解說會為您介紹 Visual Studio 中的 Office Developer Tools，以及 VSTO 增益集的程式撰寫模型。  
  
 如需引導您完成 Office 專案中一些常見工作的主題清單，請參閱 [Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [使用者入門 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)  
  
  