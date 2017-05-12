---
title: "逐步解說：建立 Word 的第一個文件層級自訂"
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
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發], 建立第一個專案"
  - "Visual Studio 中的 Office 程式開發, 建立第一個專案"
  - "Word [Visual Studio 中的 Office 程式開發], 建立第一個專案"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 逐步解說：建立 Word 的第一個文件層級自訂
  本入門逐步解說將示範如何建立 Microsoft Office Word 的文件層級自訂。  只有在特定的文件開啟時，才能使用您在這種解決方案中建立的功能。  您不能使用文件層級自訂來進行應用程式層級的變更，例如在任何文件開啟時顯示新功能區索引標籤。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Word 文件專案。  
  
-   將文字加入 Visual Studio 設計工具裝載的文件。  
  
-   撰寫可使用 Word 物件模型的程式碼，該程式碼會在自訂文件開啟時將文字加入此文件。  
  
-   建置和執行專案來進行測試。  
  
-   清除專案，將不需要的組建檔案和安全性設定從開發電腦上移除。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## 建立專案  
  
#### 在 Visual Studio 中建立新的 Word 文件專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  在範本窗格中，展開 \[Visual C\#\] 或 \[Visual Basic\]，然後展開 \[Office\/SharePoint\]。  
  
4.  在展開的 \[Office\/SharePoint\] 節點下，選取 \[Office 增益集\] 節點。  
  
5.  在專案範本清單中，選取 Word VSTO 文件專案。  
  
6.  在 \[名稱\] 方塊中輸入 **FirstDocumentCustomization**。  
  
7.  按一下 \[**確定**\]。  
  
     隨即開啟 \[Visual Studio Tools for Office 專案精靈\]。  
  
8.  選取 \[建立新文件\]，然後按一下 \[確定\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立 **FirstDocumentCustomization** 專案，並在專案中加入 **FirstDocumentCustomization** 文件和 ThisDocument 程式碼檔。  **FirstDocumentCustomization** 文件會自動在設計工具中開啟。  
  
## 在設計工具中關閉並重新開啟文件  
 如果您在開發專案時故意或不小心關閉了設計工具中的文件，您都可以重新開啟它。  
  
#### 在設計工具中關閉並重新開啟文件  
  
1.  請按一下設計工具視窗的 \[關閉\] 按鈕 \(X\)，關閉文件。  
  
2.  在 \[方案總管\] 中，以滑鼠右鍵按一下 **ThisDocument** 程式碼檔案，然後按一下 \[設計工具檢視\]。  
  
     \-或\-  
  
     按兩下 \[方案總管\] 中的 **ThisDocument** 程式碼檔案。  
  
## 在設計工具中將文字加入文件  
 您可以修改設計工具中開啟的文件，藉此設計自訂的使用者介面 \(UI\)。  例如，您可以加入文字、表格或 Word 控制項。  如需如何使用設計工具的詳細資訊，請參閱[在 Visual Studio 環境下的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
#### 使用設計工具將文字加入文件  
  
1.  在設計工具開啟的文件中，輸入下列文字。  
  
     **This text was added by using the designer.**  
  
## 以程式設計方式將文字加入文件  
 接著，將程式碼加入 ThisDocument 程式碼檔。  新程式碼會使用 Word 物件模型，將第二段的文字加入文件。  ThisDocument 程式碼檔預設包含下列產生的程式碼：  
  
-   `ThisDocument` 類別的部分定義，此定義代表該文件的程式設計模型，而且會提供 Word 物件模型的存取。  如需詳細資訊，請參閱[Document 主項目](../vsto/document-host-item.md)與 [Word 物件模型概觀](../vsto/word-object-model-overview.md)。  `ThisDocument` 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   `ThisDocument_Startup` 和 `ThisDocument_Shutdown` 事件處理常式。  開啟和關閉文件時會呼叫這些事件處理常式。  請使用這些事件處理常式，在文件開啟時初始化自訂，以及在文件關閉時清除自訂所用的資源。  如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
#### 使用程式碼將第二段文字加入文件  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[ThisDocument\]，然後按一下 \[檢視程式碼\]。  
  
     程式碼檔案隨即在 Visual Studio 中開啟。  
  
2.  以下列程式碼取代 `ThisDocument_Startup` 事件處理常式。  開啟文件時，這段程式碼會將第二段文字加入文件。  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  這個程式碼會使用索引值 1 存取 <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> 屬性的第一個段落。  雖然 Visual Basic 和 Visual C\# 都是使用以 0 為起始的陣列，但是在 Word 物件模型中，大多數集合的陣列界限下限都是 1。  如需詳細資訊，請參閱[撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)。  
  
## 測試專案  
  
#### 測試文件  
  
1.  按 **F5** 建置及執行專案。  
  
     當您建置專案時，程式碼會編譯為與文件相關聯的組件。  Visual Studio 會將文件複本和組件置於專案的建置輸出資料夾中，而且會設定開發電腦中的安全性設定以執行自訂。  如需詳細資訊，請參閱 [建置 Office 方案](../vsto/building-office-solutions.md)。  
  
2.  確認文件中出現下列文字。  
  
     **This text was added by using the designer.**  
  
     **This text was added by using code.**  
  
3.  關閉文件。  
  
## 清除 Project  
 當您完成專案開發時，必須移除建置輸出資料夾中的檔案和建置程序建立的安全性設定。  
  
#### 清除開發電腦上已完成的專案  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[清除方案\]。  
  
## 後續步驟  
 現在您已經建立 Word 的基本文件層級自訂，可以從下列主題進一步了解如何開發自訂：  
  
-   您可以在文件層級自訂中執行的一般程式設計工作：[文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)。  
  
-   Word 文件層級自訂專屬的程式設計工作：[Word 方案](../vsto/word-solutions.md)。  
  
-   使用 Word 物件模型：[Word 物件模型概觀](../vsto/word-object-model-overview.md)。  
  
-   自訂 Word 的 UI，例如，將自訂索引標籤加入功能區，或建立您專屬的執行窗格：[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
-   使用 Visual Studio 中的 Office 解決方案提供的擴充 Word 物件，執行無法使用 Word 物件模型完成的工作 \(例如，在文件上裝載 Managed 控制項，以及使用 Windows Form 資料繫結模型將 Word 控制項繫結至資料\)：[使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)。  
  
-   建置和偵錯 Word 文件層級自訂：[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
-   部署 Word 文件層級自訂：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word 方案](../vsto/word-solutions.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  