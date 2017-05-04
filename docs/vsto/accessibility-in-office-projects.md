---
title: "Office 專案中的協助工具 | Microsoft Docs"
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
  - "網頁可及性 [Visual Studio 中的 Office 程式開發]"
  - "Visual Studio 中的 Office 程式開發, 網頁可及性"
  - "功能區 [Visual Studio 中的 Office 程式開發], 快速鍵"
  - "快速鍵 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Office 專案中的協助工具
  Microsoft Visual Studio 和 Microsoft Office 提供許多協助工具功能，可讓您建置 \(Build\) 符合標準協助工具需求的自訂方案。  Microsoft 在 Web 上發行了一些協助工具指南。  如需詳細資料，請參閱[協助工具網站](http://go.microsoft.com/fwlink/?LinkID=37113) \(英文\)。  
  
 在大部分情況下，Visual Studio 中的 Office 專案都能符合協助工具標準，或是公開可供您設定的屬性，以增加方案的使用性。  不過，某些功能的可及性會受到限制。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 設計階段的協助工具  
  
### 在文件層級專案中使用快速鍵  
 在 Visual Studio 中開啟 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿時，一次只有一個應用程式會收到快速鍵命令。  根據預設，Visual Studio 會接收所有快速鍵命令，不過您可選取 \[**選項**\] 對話方塊裡 \[**鍵盤設定**\] 頁面上的 \[**動態鍵盤配置**\]，使 Word 或 Excel 在文件取得焦點 \(Focus\) 時接收快速鍵命令。  如需詳細資訊，請參閱[選項對話方塊、Microsoft Office 鍵盤設定、Microsoft Office Word 鍵盤](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)與[選項對話方塊、Microsoft Office 鍵盤設定、Microsoft Office Excel 鍵盤](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)。  
  
### 針對文件層級專案中的功能區顯示快速鍵  
 在 Visual Studio 中開啟 Word 文件或 Excel 活頁簿時，您無法在功能區按下 Alt 鍵來檢視索引標籤和控制項的快速鍵。  若要在使用設計工具開啟文件或活頁簿時檢視快速鍵，請執行下列步驟。  
  
##### 若要檢視設計工具中功能區索引標籤和控制項的快速鍵  
  
1.  在 Visual Studio 中，按一下 \[**工具**\] 功能表的 \[**選項**\]。  
  
2.  展開 \[**Office 工具**\] 節點，然後依需要選取 \[**Microsoft Office Excel 鍵盤**\] 或 \[**Microsoft Office Word 鍵盤**\]。  
  
3.  選取 \[**動態鍵盤配置**\]。  
  
     這時會出現一則訊息，告知您必須重新啟動 Visual Studio 以讓變更生效。  
  
4.  按一下 \[**確定**\]。  
  
5.  重新啟動 Visual Studio，然後重新開啟專案。  
  
6.  開啟您的專案所需的文件或活頁簿設計工具。  
  
7.  按 F6 顯示功能區快速鍵。  
  
## 執行階段的協助工具  
  
### Office 文件上的 Windows Form 控制項  
 Windows Form 控制項會公開可及性屬性，以提供有關控制網頁可及性 \(如螢幕助讀員\) 的資訊。  當控制項位於文件層級自訂中的 Office 文件上時，您便可利用這些協助工具屬性。  如需詳細資訊，請參閱[為 Windows Form 上的控制項提供可及性資訊](../Topic/Providing%20Accessibility%20Information%20for%20Controls%20on%20a%20Windows%20Form.md)。  
  
 不過，當 Windows Form 控制項裝載到 Excel 活頁簿或 Word 文件上時，協助工具會在執行階段受到一些限制：  
  
-   您無法使用定位鍵在控制項之間移動。  
  
-   當您將文件的縮放設定變更為 100% 以外的設定時，會停用文件上的控制項。  
  
 如需文件上 Windows Form 控制項限制的詳細資訊，請參閱 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  
  
### 執行窗格和自訂工作窗格  
 當執行窗格或自訂工作窗格取得焦點時，可以像存取 Windows Form 應用程式上的控制項一樣存取其上的控制項。  若要在執行窗格和文件之間移動游標，可按 **F6**。  
  
 如需執行窗格和自訂工作窗格的詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)和[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
### 顯示模式  
 Visual Studio 具有下列與顯示模式相關的限制：  
  
-   當您將文件的縮放設定變更為 100% 以外的設定時，會停用 Word 文件或 Excel 工作表上的控制項。  
  
-   如果使用者將電腦的可及性選項變更為 \[**使用高對比**\]，\[**新增專案**\] 對話方塊便不會正確顯示控制項。  
  
 您可以使用 \[放大鏡\] 克服這些限制。  \[放大鏡\] 是 Windows 的顯示公用程式，它會開啟另一個視窗來顯示螢幕上某個放大的部分。  
  
## 請參閱  
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [適用於行動不便人士的協助工具](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Visual Studio 的協助工具功能](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  