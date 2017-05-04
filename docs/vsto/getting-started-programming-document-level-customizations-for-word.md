---
title: "Word 文件層級自訂的程式設計入門 | Microsoft Docs"
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
  - "Word 專案 [Visual Studio 中的 Office 程式開發], 使用者入門"
  - "Visual Studio 中的 Word 方案"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Word 文件層級自訂的程式設計入門
  如果您才剛開始使用建立適用於 Microsoft Office Word 的文件層級自訂中使用 Visual Studio，本主題包含您需要知道的資訊。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## 了解 Word 文件層級自訂運作的方式  
 您建立的每個 Word 自訂都是以單一文件做為基礎。  若要開始使用該自訂，使用者可以開啟文件或是從 Word 範本建立文件。  文件中的事件，例如將游標滑入特定區域或按一下按鈕和功能表項目，都可以呼叫組件 \(Assembly\) 中的事件處理方法。  當文件關閉時，就無法在 Word 中使用自訂所提供的功能。  
  
 如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## 建立 Word 文件層級專案  
 若要建立 Word 的文件層級自訂，請在 \[**新增專案**\] 對話方塊中使用 \[Word 文件\] 或 \[Word 範本\] 專案範本。  這些範本包括必要的組件參考和專案檔。  
  
 如需如何建立 Word 文件層級專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  如需專案範本的詳細資訊，請參閱 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)。  
  
## 使用主項目主控制項進行 Word 文件的程式設計  
 「*主項目*」\(Host Item\) 和「*主控制項*」\(Host Control\) 類別 \(Class\) 都可為文件層級自訂提供程式撰寫模型 \(Programming Model\)。  
  
 主項目提供程式碼的進入點，，而且可做為主控制項和 Windows Form 控制項的容器。  在 Word 的文件層級專案中，主項目是以 `ThisDocument` 類別表示。  
  
 主控制項是以原生 Word 物件為基礎，例如內容控制項、書籤與 XML 節點。  主控制項提供與原生 Word 物件類似的功能，但是同時具有新事件、設計工具支援與資料繫結功能。  在專案程式碼和 IntelliSense 中，主控制項會顯示為第一級物件，因此不需要巡覽 Word 物件模型，就可以輕鬆地在程式碼中直接參考特定物件。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)  
  
-   [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
## 自訂 Word 的使用者介面  
 大部分的 Microsoft Office 方案都會修改 Office 應用程式的使用者介面 \(UI\)，以提供一些讓使用者與方案互動的方法。  使用文件層級自訂修改 Word UI 的方法很多。  例如，您可以將控制項加入至功能區，因此，您可以顯示執行窗格。  如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 您也可以直接在 Visual Studio 中開啟與專案相關聯的文件。  文件在 Visual Studio 中開啟時，您可以使用 Word 使用者介面修改文件。  您也可以使用文件做為設計介面，好讓您將控制項拖曳至文件。  如需詳細資訊，請參閱[在 Visual Studio 環境下的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 將控制項繫結至資料  
 內容控制項和 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項都是位於控制項清單中，方便您直接從 \[**資料來源**\] 視窗拖曳。  以這種方式加入內容控制項和書籤，會自動將它們繫結至利用視窗設定的資料來源。  您不需要撰寫任何程式碼，就可以顯示來自資料庫、服務和商務物件的資料。  如需詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## 後續步驟  
 若要了解如何建立 Word 文件層級自訂的詳細資訊，請參閱[逐步解說：建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)。  此逐步解說將為您介紹 Visual Studio 中的 Office 開發工具，以及 Word 文件層級自訂的程式撰寫模型。  
  
 如需逐步執行 Word 專案中一些常見工作的主題清單，請參閱 [Office 程式設計的一般工作](../vsto/common-tasks-in-office-programming.md)。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [Word 方案](../vsto/word-solutions.md)   
 [逐步解說：建立 Word 的第一個文件層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  