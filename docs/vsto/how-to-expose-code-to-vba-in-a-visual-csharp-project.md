---
title: "如何：公開程式碼給 Visual C# 專案中的 VBA"
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
  - "VBA [Visual Studio 中的 Office 程式開發], 在文件層級自訂中公開程式碼"
  - "Visual C# [Visual Studio 中的 Office 程式開發], 將程式碼公開到 VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：公開程式碼給 Visual C# 專案中的 VBA
  如果您想讓 Visual C\# 專案中的程式碼和 Visual Basic for Applications \(VBA\) 程式碼彼此互動，可以將 Visual C\# 專案中的程式碼公開 \(Expose\) 給 Visual Basic for Applications \(VBA\) 程式碼。  
  
 Visual C\# 程序與 Visual Basic 程序不同。  如需詳細資訊，請參閱[如何：公開程式碼給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 公開 Visual C\# 專案中的程式碼  
 若要讓 VBA 程式碼呼叫 Visual C\# 專案中的程式碼，請修改程式碼，讓 COM 可以看到該程式碼，然後在設計工具中將 \[**ReferenceAssemblyFromVbaProject**\] 屬性設定為 \[**True**\]。  
  
 如需示範如何從 VBA 呼叫 Visual C\# 專案中之方法的逐步解說，請參閱[逐步解說：在 Visual C&#35; 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。  
  
#### 若要將 Visual C\# 專案中的程式碼公開給 VBA  
  
1.  開啟或建立以支援巨集的 Word 文件、Excel 活頁簿或 Excel 範本為基礎，而且已包含 VBA 程式碼的文件層級專案。  
  
     如需支援巨集的文件檔案格式之詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能不適用於 Word 範本專案。  
  
2.  確定文件中的 VBA 程式碼可以執行，而不需提示使用者啟用巨集。  您可以將 Office 專案的位置加入至 Word 或 Excel 之 \[信任中心\] 設定中的信任位置清單，藉以信任要執行的 VBA 程式碼。  
  
3.  將想要公開給 VBA 的成員加入至專案的公用 \(Public\) 類別，並將新成員宣告為 **public**。  
  
4.  將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性套用至要公開給 VBA 的類別。  這些屬性可以讓 COM 看到類別，但是不會產生類別介面。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  覆寫專案中主項目類別的 **GetAutomationObject** 方法，以傳回要公開給 VBA 的類別執行個體 \(Instance\)：  
  
    -   如果要將主項目類別公開給 VBA，請覆寫屬於這個類別的 **GetAutomationObject** 方法，並傳回類別的目前執行個體。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   如果要將不是主項目的類別公開給 VBA，請覆寫專案中任何主項目的 **GetAutomationObject** 方法，並傳回非主項目類別的執行個體。  例如，下列程式碼假設您要將名為 `DocumentUtilities` 的類別公開給 VBA。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     如需主項目的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
6.  從要公開給 VBA 的類別中擷取介面。  在 \[**擷取介面**\] 對話方塊中，選取想要併入介面宣告中的公用成員。  如需詳細資訊，請參閱[Extract Interface Refactoring &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md)。  
  
7.  將 **public** 關鍵字加入至介面宣告。  
  
8.  將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性加入至介面，讓 COM 可以看到介面。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的設計工具中，開啟文件 \(Word\) 或工作表 \(Excel\)。  
  
10. 在 \[**屬性**\] 視窗中，選取 \[**ReferenceAssemblyFromVbaProject**\] 屬性，然後將值變更為 \[**True**\]。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或文件中的 VBA 程式碼未受到信任無法執行，則您會在將 \[**ReferenceAssemblyFromVbaProject**\] 屬性設定為 \[**True**\] 時收到錯誤訊息。  這是因為在這個情況下，Visual Studio 無法修改文件中的 VBA 專案。  
  
11. 按一下訊息中顯示的 \[**確定**\]。  這則訊息是要提醒您，如果從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 執行專案時將 VBA 程式碼加入至活頁簿或文件，則 VBA 程式碼會在下次建置 \(Build\) 專案時遺失。  這是因為每次建置專案時都會覆寫建置輸出資料夾中的文件。  
  
     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫組件。  Visual Studio 也會將名為 `GetManagedClass` 的方法加入至 VBA 專案。  您可以從 VBA 專案的任何位置呼叫這個方法，以存取公開給 VBA 的類別。  
  
12. 建置專案。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說：在 Visual C&#35; 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [如何：公開程式碼給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  