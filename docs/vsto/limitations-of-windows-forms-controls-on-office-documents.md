---
title: "Office 文件上的 Windows Form 控制項限制 | Microsoft Docs"
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
  - "ActiveX 控制項 [Visual Studio 中的 Office 程式開發]"
  - "控制項 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "工具箱 [Visual Studio 中的 Office 程式開發], 不支援的控制項"
  - "使用者控制項 [Visual Studio 中的 Office 程式開發], 群組控制項"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], ActiveX 舊版"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], 限制"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], 工具箱"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], 不支援的屬性和方法"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Office 文件上的 Windows Form 控制項限制
  加入至 Microsoft Office Word 文件或 Microsoft Office Excel 工作表的 Windows Form 控制項，與加入至 Windows Form 的 Windows Form 控制項之間有一些不同。  例如，將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項加入至文件時，屬性 \(例如 <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>、<xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> 和 <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A>\) 不會表現如您預期的行為。  
  
 當中多數差異是因為將 Windows Form 控制項裝載到文件的方式所造成。  將 Windows Form 控制項加入至文件時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會嵌入之後將 Windows Form 控制項裝載到文件中的 ActiveX 控制項。  Windows Form 控制項不會直接嵌入文件。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Windows Form 控制項的方法和屬性限制  
 Windows Form 控制項的許多方法和屬性在文件上的運作方式與在 Windows Form 上不同，因此建議不使用它們。  例如，設定屬性 \(例如 `Dock` 和 `Anchor`\) 只會影響有關容器 ActiveX 控制項之控制項的位置，而不會影響文件的位置。  下面列出 Word 和 Excel 中不支援 Windows Form 控制項的方法和屬性：  
  
-   不支援 Excel 控制項的方法和屬性：  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   不支援 Word 控制項的方法和屬性：  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 您也無法設定依照 Word 文件上文字排列之 Windows Form 控制項的 `Left` 或 `Top` 屬性。  在下列情況中，Windows Form 控制項會依照文字排列方式加入：  
  
-   您用程式設計的方式將控制項加入至 Word 文件，並使用可指定位置範圍的方法。  
  
-   您在執行階段將 Windows Form 控制項加入至 Word 文件。  您可以使用設計工具修改控制項，變更這項作業。  
  
## Office 文件上 Windows Form 控制項差異  
 通常 Windows Form 控制項在 Office 文件和 Windows Form 上的行為表現相同，但仍存在一些差異。  下表說明 Windows Form 控制項在 Office 文件上具有的差異：  
  
|功能|差異|  
|--------|--------|  
|控制項索引標籤順序|您無法定位 Excel 工作表或 Word 文件上的控制項。|  
|控制項群組|您無法使用 <xref:System.Windows.Forms.GroupBox> 控制項包含 Office 文件上的其他控制項。  當您將多個選項按鈕直接加入文件中時，這些選項按鈕並不會互斥。  您可以撰寫程式碼讓選項按鈕互斥，但最好是能先將選項按鈕加入至使用者控制項，然後再將該使用者控制項加入至文件中。  如需詳細資訊，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Word 控制項範例＞或＜Excel 控制項範例＞。|  
|控制項型別|文件中使用的 Windows Form 控制項包裝在 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的類別中，該類別賦予控制項 Excel 工作表或 Word 文件專用的其他功能。  例如，如果您在 Excel 工作表上有 `Button` 控制項，在參考或轉換物件時，請務必將型別指定為 <xref:Microsoft.Office.Tools.Excel.Controls.Button>，而不是 <xref:System.Windows.Forms.Button>。|  
|控制項位置和大小|控制項的大小和位置是由屬於容器 ActiveX 控制項一部分的屬性來決定。  ActiveX 控制項屬性採用的值，與 Windows Form 控制項對等屬性採用的值不同。  設定控制項的 `Top`、`Left`、`Height` 或 `Width` 屬性時，度量單位會是點數，而不是像素。|  
|Word 文件上的控制項位置|如果將控制項加入至流程配置，請記住，控制項會在內容變更時跟著內容一起流動。  從 \[**工具箱**\] 拖曳控制項時，因為它是跟著文字排列一起加入至 Word 文件，所以您無法將該控制項錨定至段落。  如果您使用其他方法加入控制項 \(例如，按兩下該控制項\)，則會根據您為插入圖片設定的 Word 選項插入控制項。<br /><br /> 您無法設定依照文字排列之控制項的 `Left` 或 `Top` 屬性。<br /><br /> 您無法在頁首、頁尾或子文件內放置控制項。|  
|控制項事件|選取控制項後，它會按下列順序引發事件：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 取消選取控制項後，它會按下列順序引發事件：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|控制項縮放比例|當文件的縮放設定變更為 100% 以外的比例時，就會停用控制項，儘管這些控制項會隨文件進行縮放。  例如，如果您在文件縮放為 130% 時按一下按鈕，則會顯示已停用控制項的訊息，直到將縮放比例設為 100% 為止。  您將縮放比例變更為 100% 時，控制項會運作正常。|  
|控制項屬性值|即使將 Windows Form 上的控制項屬性設為整數值，Word 文件上的控制項仍會設為單精度。  在 Excel 中，控制項的屬性值設為雙精度。  如果工作表上控制項的 `Height` 和 `Width` 屬性超出了工作表或螢幕的大小，則會將值截斷。|  
|調整控制項大小|如果您使用八個縮放控點中的其中一個縮放控點調整文件上控制項的大小，則在重新選取該控制項之前，不會在 \[**屬性**\] 視窗中反映新的控制項維度。|  
|控制項行為|當 \[工作表\] 視窗為分隔狀態時，Excel 工作表上的控制項可能不會正常運作。  例如，也許只能在其中一個視窗內存取工作表上的 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>。|  
|控制項命名|您無法使用保留字為控制項命名。  例如，如果將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 加入至工作表，並將名稱變更為 **System**，則會在建置專案時會發生錯誤。|  
|以程式設計的方式加入至控制項|請勿在執行階段使用控制項的建構函式 \(Constructor\) 將控制項加入至文件。  請改用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 所提供的 Helper 方法。  例如，使用 <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> 方法將按鈕加入至工作表。  如果這些 Helper 方法不支援您要加入的控制項，則可以使用 AddControl 方法。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。|  
|複製控制項|如果您在執行階段複製 Windows Form 控制項並將其貼至文件，則會將一個空的容器 ActiveX 控制項貼至該文件。  Windows Form 控制項不會出現在新位置，也不會將原始控制項的後置程式碼複製到容器 ActiveX 控制項。|  
  
## 文件層級專案的限制  
 對於在文件上使用 Windows Form 控制項，文件層級專案有些特有限制。  
  
### 設計階段的控制項支援  
 在 Visual Studio 設計工具中開啟 Excel 工作表或 Word 文件時，會移除 \[**工具箱**\] 中的某些特定 Windows Form 控制項。  這是因為技術限制，或是因為 Word 或 Excel 內已提供此功能。  Excel 和 Word 專案支援文件取得焦點時，出現在 \[**工具箱**\] 中的所有 Windows Form 控制項及其他元件，您也可以將協力廠商控制項加入至工作表或文件。  
  
> [!NOTE]  
>  文件受保護時，會移除 \[**工具箱**\] 中的所有控制項。  如需文件保護的詳細資訊，請參閱[文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)。  
  
> [!NOTE]  
>  協力廠商控制項的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性必須設定為 **true**，才能夠在 Office 方案中使用。  
  
 下列控制項和元件無法在 \[**工具箱**\] 中使用：  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### 支援舊版 ActiveX 控制項  
 如果您建立的文件層級 Office 專案使用包含 ActiveX 控制項的現有 Word 文件或 Excel 活頁簿，則 ActiveX 控制項的功能不會喪失；不過，不支援從 Visual Studio 內將新的 ActiveX 控制項加入至文件。  例如，如果您的 Word 文件有一個可以執行 Visual Basic for Applications \(VBA\) 巨集的 \[**控制項**\] 工具箱按鈕，則在 Office 專案中使用文件後，此控制項將會繼續執行該巨集。  不過，建議您移除 ActiveX 控制項和 VBA 巨集，並使用 Windows Form 控制項和 Managed 程式碼取代它們。  
  
## 請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  