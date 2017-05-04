---
title: "Excel 文件層級自訂的程式設計入門 | Microsoft Docs"
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
  - "Excel 專案 [Visual Studio 中的 Office 程式開發], 使用者入門"
  - "Visual Studio 中的 Excel 方案"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Excel 文件層級自訂的程式設計入門
  如果您才剛開始使用建立適用於 Microsoft Office Excel 的文件層級自訂中使用 Visual Studio，本主題包含您需要知道的資訊。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## 了解 Excel 文件層級自訂運作的方式  
 Excel 文件層級自訂是以單一活頁簿為基礎。  若要開始使用該自訂，使用者可以開啟活頁簿或是從 Excel 範本建立活頁簿。  活頁簿中的事件，例如在儲存格中輸入資料或按一下按鈕和功能表項目，都可以呼叫組件中的事件處理方法。  當活頁簿關閉時，自訂所提供的功能就無法在 Excel 中，只有在包含其文件。  
  
 如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## 建立 Excel 文件層級專案  
 若要建立 Excel 的文件層級自訂，請在 \[**新增專案**\] 對話方塊中使用 \[Excel 活頁簿\] 或 \[Excel 範本\] 專案範本。  這些範本包括必要的組件參考和專案檔。  
  
 如需如何建立 Excel 文件層級專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  如需專案範本的詳細資訊，請參閱 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## 使用主項目和主控制項來進行 Excel 活頁簿的程式設計  
 *主* 項目和 *主控制項* 是文件層級自訂提供程式撰寫模型以 Visual Studio 建立的類別。  
  
 主項目提供程式碼的進入點，，而且可做為主控制項和 Windows Form 控制項的容器。  在 Excel 文件層級專案中，這些主項目是以 `ThisWorkbook`、`Sheet1`、`Sheet2` 和 `Sheet3` 類別表示。  
  
 主控制項是以原生 Excel 物件為基礎，例如清單物件和範圍。  主控制項可對原生 Excel 物件提供類似的功能，但是它們同時具有新事件、設計工具支援和資料繫結功能。  在專案程式碼和 IntelliSense 中，主控制項會顯示為第一級物件，因此不需要巡覽 Excel 物件模型，就可以輕鬆地在程式碼中直接參考特定物件。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)  
  
-   [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
## 自訂 Excel 的使用者介面  
 大部分的 Microsoft Office 方案都會修改 Office 應用程式的使用者介面 \(UI\)，以提供一些讓使用者與方案互動的方法。  藉由使用文件層級自訂，您有很多種修改 Excel UI 的方法可以選用。  例如，您可以將控制項加入至功能區，也可以顯示執行窗格。  如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 您也可以直接在 Visual Studio 中開啟與專案相關聯的活頁簿。  活頁簿在 Visual Studio 中開啟時，您可以使用 Excel 使用者介面修改活頁簿。  您也可以使用活頁簿做為設計介面，好讓您將控制項拖曳至工作表。  如需詳細資訊，請參閱[在 Visual Studio 環境下的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 使用資料繫結  
 主控制項也會列入控制項清單中，您可以直接從 \[**資料來源**\] 視窗中拖曳。  以這種方式加入主控制項，會自動將主控制項繫結至利用視窗設定的資料來源。  您不需要撰寫任何程式碼，您可以顯示來自資料庫、Web 服務和商務物件的資料。  如需詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## 後續步驟  
 若要了解如何建立 Excel 文件層級自訂的詳細資訊，請參閱[逐步解說：建立 Excel 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。  此逐步解說將為您介紹 Visual Studio 中的 Office 開發工具，以及 Excel 文件層級自訂的程式撰寫模型。  
  
 如需逐步執行 Excel 專案中一些常見工作的主題清單，請參閱 [Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [Excel 方案](../vsto/excel-solutions.md)   
 [逐步解說：建立 Excel 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  