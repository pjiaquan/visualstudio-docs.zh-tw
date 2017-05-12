---
title: "如何：公開程式碼給 Visual Basic 專案中的 VBA"
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
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發], 公開程式碼"
  - "將程式碼公開到 VBA"
  - "主項目 [Visual Studio 中的 Office 程式開發], 將程式碼公開到 VBA"
  - "VBA [Visual Studio 中的 Office 程式開發], 在文件層級自訂中公開程式碼"
  - "Visual Basic [Visual Studio 中的 Office 程式開發], 將程式碼公開到 VBA"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：公開程式碼給 Visual Basic 專案中的 VBA
  如果您想讓 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案中的程式碼和 Visual Basic for Applications \(VBA\) 程式碼彼此互動，可以將專案中的程式碼公開 \(Expose\) 給 Visual Basic for Applications \(VBA\) 程式碼。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic 程序與 Visual C\# 程序不同。  如需詳細資訊，請參閱[如何：公開程式碼給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。  
  
 主項目類別 \(Class\) 中程式碼採用的程序，與其他類別中程式碼採用的程序不同：  
  
-   [公開主項目類別中的程式碼](#HostItemCode)  
  
-   [公開不在主項目類別中的程式碼](#NonHostItem)  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需觀看相關示範影片，請參閱[如何：從 VBA 呼叫 VSTO 程式碼？](http://go.microsoft.com/fwlink/?LinkId=136757)\(英文\)。  
  
##  <a name="HostItemCode"></a> 公開主項目類別中的程式碼  
 若要讓 VBA 程式碼呼叫主項目類別中的 Visual Basic 程式碼，請將主項目的 \[**EnableVbaCallers**\] 屬性設定為 \[**True**\]。  
  
 如需示範如何公開主項目類別方法然後從 VBA 加以呼叫的逐步解說，請參閱[逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。  如需主項目的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
#### 若要將主項目中的程式碼公開給 VBA  
  
1.  開啟或建立以支援巨集的 Word 文件、Excel 活頁簿或 Excel 範本為基礎，而且已包含 VBA 程式碼的文件層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案。  
  
     如需支援巨集的文件檔案格式之詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能不適用於 Word 範本專案。  
  
2.  確定文件中的 VBA 程式碼可以執行，而不需提示使用者啟用巨集。  您可以將 Office 專案的位置加入至 Word 或 Excel 之 \[信任中心\] 設定中的信任位置清單，藉以信任要執行的 VBA 程式碼。  
  
3.  將想要公開給 VBA 的屬性、方法或事件加入至專案中的其中一個主項目類別，並將新成員宣告為 **Public**。  類別名稱是取決於應用程式：  
  
    -   在 Word 專案中，主項目類別預設會命名為 `ThisDocument`。  
  
    -   在 Excel 專案中，主項目類別預設會命名為 `ThisWorkbook`、`Sheet1`、`Sheet2` 和 `Sheet3`。  
  
4.  將主項目的 \[**EnableVbaCallers**\] 屬性設定為 \[**True**\]。  在設計工具中開啟主項目時，這個屬性就會出現在 \[**屬性**\] 視窗中。  
  
     設定這個屬性之後，Visual Studio 會自動將 \[**ReferenceAssemblyFromVbaProject**\] 屬性設定為 **True**。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或文件中的 VBA 程式碼未受到信任無法執行，則會在將 \[**EnableVbaCallers**\] 屬性設定為 \[**True**\] 時接收到錯誤訊息。  這是因為在這個情況下，Visual Studio 無法修改文件中的 VBA 專案。  
  
5.  按一下訊息中顯示的 \[**確定**\]。  這則訊息是要提醒您，如果從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 執行專案時將 VBA 程式碼加入至活頁簿或文件，則 VBA 程式碼會在下次建置專案時遺失。  這是因為每次建置專案時都會覆寫建置輸出資料夾中的文件。  
  
     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫組件。  Visual Studio 也會將名為 `CallVSTOAssembly` 的屬性加入至 VBA 專案中的 `ThisDocument`、`ThisWorkbook`、`Sheet1`、`Sheet2` 或 `Sheet3` 模組。  您可以使用這個屬性存取已公開至 VBA 的類別公用成員。  
  
6.  建置專案。  
  
##  <a name="NonHostItem"></a> 公開不在主項目類別中的程式碼  
 若要讓 VBA 程式碼呼叫不在主項目類別中的 Visual Basic 程式碼，請修改程式碼，讓 VBA 可以看到程式碼。  
  
#### 若要將不在主項目類別中的程式碼公開給 VBA  
  
1.  開啟或建立以支援巨集的 Word 文件、Excel 活頁簿或 Excel 範本為基礎，而且已包含 VBA 程式碼的文件層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案。  
  
     如需支援巨集的文件檔案格式之詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能不適用於 Word 範本專案。  
  
2.  確定文件中的 VBA 程式碼可以執行，而不需提示使用者啟用巨集。  您可以將 Office 專案的位置加入至 Word 或 Excel 之 \[信任中心\] 設定中的信任位置清單，藉以信任要執行的 VBA 程式碼。  
  
3.  將想要公開給 VBA 的成員加入至專案的公用 \(Public\) 類別，並將新成員宣告為 **public**。  
  
4.  將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 <xref:Microsoft.VisualBasic.ComClassAttribute> 屬性套用至要公開給 VBA 的類別。  這些屬性讓 VBA 可以看到這個類別。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  覆寫專案裡主項目類別的 **GetAutomationObject** 方法，以傳回要公開給 VBA 的類別執行個體 \(Instance\)。  下列程式碼範例假設您要將 `DocumentUtilities` 類別公開給 VBA。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，開啟文件 \(Word\) 或工作表 \(Excel\) 設計工具。  
  
7.  在 \[**屬性**\] 視窗中，選取 \[**ReferenceAssemblyFromVbaProject**\] 屬性，然後將值變更為 \[**True**\]。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或文件中的 VBA 程式碼未受到信任無法執行，則會在將 \[**ReferenceAssemblyFromVbaProject**\] 屬性設定為 \[**True**\] 時接收到錯誤訊息。  這是因為在這個情況下，Visual Studio 無法修改文件中的 VBA 專案。  
  
8.  按一下訊息中顯示的 \[**確定**\]。  這則訊息是要提醒您，如果從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 執行專案時將 VBA 程式碼加入至活頁簿或文件，則 VBA 程式碼會在下次建置專案時遺失。  這是因為每次建置專案時都會覆寫建置輸出資料夾中的文件。  
  
     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫組件。  Visual Studio 也會將名為 `GetManagedClass` 的方法加入至 VBA 專案。  您可以從 VBA 專案的任何位置呼叫這個方法，以存取公開給 VBA 的類別。  
  
9. 建置專案。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [如何：公開程式碼給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  