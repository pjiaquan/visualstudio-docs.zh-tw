---
title: "文件層級方案的文件保護"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "使用權限 [Visual Studio 中的 Office 程式開發]"
  - "受限制的使用權限 [Visual Studio 中的 Office 程式開發]"
  - "活頁簿 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 文件層級方案的文件保護
  您可以在文件層級專案中使用 Microsoft Office Word 和 Microsoft Office Excel 的保護功能。  這些功能會防止未授權的使用者變更文件中受保護的部分。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用 Excel，可以於活頁簿在設計工具中開啟時開啟及關閉保護；  使用 Word，則只能在設計工具之外開啟保護。  您可以在執行階段，以程式啟用或停用 Word 和 Excel 的保護功能。  
  
 設計工具中，開啟的文件之文件保護功能啟用時，所有控制項都會從 \[**工具箱**\] 移除，或是變成無法使用，如此您就無法從 \[**資料來源**\] 視窗拖曳任何項目至文件中。  
  
## ServerDocument 和受保護的文件  
 如果文件受到保護，就無法從文件外部存取資料快取。  您不能使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別擷取或操作受保護文件中快取的資料，也不能使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> 類別的其他方法。  
  
## 設計工具中的 Word 文件保護  
 在 Visual Studio 中開啟 Word 文件或範本時，如果加上保護，就不能在設計工具中開始強制使用保護功能。  Visual Studio 中，文件在開啟的期間是處於設計模式，必須在執行模式中，才可以開始強制使用保護功能。  
  
 不過，如果您所建立的專案是使用已啟用保護功能的現有 Word 文件，則在設計工具中開啟文件時，文件就會受到保護。  您不能編輯文件中受保護的部分，但是仍然可以在程式碼編輯器中撰寫程式碼，讓文件自動化。  Visual Studio 中，文件在開啟的期間如果已經啟用保護功能，也不能建置專案。  
  
 文件在設計工具中開啟的期間，您可以關閉保護功能，以便編輯文件並建置專案。  進行偵錯時，則不能在設計工具中關閉文件複本的保護功能；在偵錯期間開啟的文件與設計工具中所開啟的文件複本不同 \(輸出複本是存放在 Visual Basic 的 \\bin 目錄中，以及 C\# 的 \\bin\\debug 目錄中\)。  
  
 如果要在以設計工具開啟的文件複本上啟用保護功能，請在 Visual Studio 中關閉專案，然後開啟專案目錄中的文件複本，再開啟保護功能。  
  
## 建置時強制使用 Word 文件保護  
 Visual Studio 會在建置程序中開始強制使用 Word 文件和範本的保護功能，以便在開啟文件進行偵錯時啟用保護功能。  文件是以空白密碼進行保護。  
  
 要在建置期間啟用保護功能，是因為如果文件 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件中有程式碼，而此事件可能會導致例外狀況或變更應用程式的行為，此程式碼就能正確進行偵錯。  如果在開啟文件以後才啟用保護功能，就無法偵錯或測試初始化程式碼。  
  
## 設定密碼  
 Visual Studio 會自動啟用保護功能，但預設不提供密碼。  如果要用密碼保護文件，您必須在部署方案以前先加入密碼。  加入密碼可以讓獲得授權的使用者從文件中移除保護，而沒有密碼，就無法輕易移除保護。  如需設定密碼的詳細資訊，請參閱特定 Office 應用程式中的 \[說明\]。  
  
## 請參閱  
 [如何：以程式設計方式保護文件及部分的文件](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何：允許程式碼在具有限制使用權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  