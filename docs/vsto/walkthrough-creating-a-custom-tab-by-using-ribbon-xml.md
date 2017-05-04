---
title: "逐步解說：使用功能區 XML 建立自訂的索引標籤 | Microsoft Docs"
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
  - "自訂索引標籤 [Visual Studio 中的 Office 程式開發]"
  - "自訂功能區, 索引標籤自訂功能區, 索引標籤"
  - "功能區 [Visual Studio 中的 Office 程式開發], 自訂"
  - "功能區 [Visual Studio 中的 Office 程式開發], 索引標籤"
  - "功能區 [Visual Studio 中的 Office 程式開發], XML"
  - "XML [Visual Studio 中的 Office 程式開發], 功能區"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 逐步解說：使用功能區 XML 建立自訂的索引標籤
  本逐步解說示範如何使用 \[功能區 \(XML\)\] 項目建立自訂功能區索引標籤。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   將按鈕加入 \[增益集\] 索引標籤。  \[增益集\] 索引標籤是功能區 XML 檔案中所定義的預設索引標籤。  
  
-   使用 \[增益集\] 索引標籤上的按鈕自動化 Microsoft Office Word。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## 建立專案  
 第一步是建立 Word VSTO 增益集專案。  您稍後將會自訂此文件的 \[增益集\] 索引標籤。  
  
#### 若要建立新的專案  
  
1.  使用名稱 MyRibbonAddIn 建立 **Word 增益集**專案。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔案，並將 **MyRibbonAddIn** 專案加入方案總管。  
  
## 建立 VSTO 增益集索引標籤  
 若要建立 \[增益集\] 索引標籤，請將 \[功能區 \(XML\)\] 項目加入您的專案中。  稍後在本逐步解說中，您將會加入一些按鈕到此索引標籤中。  
  
#### 建立增益集索引標籤  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  選取 \[加入新項目\] 對話方塊中的 \[功能區 \(XML\)\]。  
  
3.  將新功能區的名稱變更為 **MyRibbon**，然後按一下 \[加入\]。  
  
     **MyRibbon.cs** 或 **MyRibbon.vb** 檔案會隨即在設計工具中開啟。  此外也會將名為 **MyRibbon.xml** 的 XML 檔案加入您的專案中。  
  
4.  在方案總管中的 **ThisAddIn.vb** 或 **ThisAddIn.cs**  檔案上按一下滑鼠右鍵，然後按一下 \[檢視程式碼\]。  
  
5.  將下列程式碼加入 **ThisAddin** 類別中。  此程式碼會覆寫 CreateRibbonExtensibilityObject 方法，並將功能區 XML 類別傳回 Office 應用程式。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  在方案總管 中的 **MyRibbonAddIn** 專案上按一下滑鼠右鍵，然後按一下 \[組建\]。  確認專案建置無誤。  
  
## 將按鈕加入增益集索引標籤中  
 此 VSTO 增益集的目標在讓使用者能夠重複使用的文字與特定資料表，加入使用中的文件。  若要提供使用者介面，可修改功能區 XML 檔案，將這兩個按鈕加入 \[增益集\] 中。  稍後在本逐步解說中，您將定義按鈕的回呼方法。  如需功能區 XML 檔案的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
#### 將按鈕加入增益集索引標籤中  
  
1.  在方案總管 中的 **MyRibbon.xml** 上按一下滑鼠按鈕，然後按一下 \[開啟\]。  
  
2.  以下列 XML 取代 **tab** 元素的內容。  此 XML 會將預設控制項群組的標籤變更為 **Content**，並加入兩個新的按鈕標籤 \[插入文字\] 及 \[插入表格\]。  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## 使用按鈕自動化文件  
 您必須加入 \[插入文字\] 及 \[插入表格\] 按鈕的 `onAction` 回呼方法，如此當使用者按一下這些按鈕時才能執行動作。  如需功能區控制項回呼方法的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
#### 加入按鈕的回呼方法  
  
1.  在方案總管 中的 **MyRibbon.cs** 或 **MyRibbon.vb** 上按一下滑鼠右鍵，然後按一下 \[開啟\]。  
  
2.  將下列程式碼加入 **MyRibbon.cs** 或 **MyRibbon.vb** 檔案的頂端。  此程式碼會建立為 <xref:Microsoft.Office.Interop.Word> 命名空間建立別名。  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  將下列方法加入 `MyRibbon` 類別中。  這是 \[插入文字\] 按鈕的回呼方法，可在使用中文件目前的游標位置上加入字串。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  將下列方法加入 `MyRibbon` 類別中。  這是 \[插入表格\] 按鈕的回呼方法，可在使用中文件目前的游標位置上加入字串。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## 測試 VSTO 增益集  
 當您執行專案時，Word 會開啟功能區上名為 \[增益集\] 的索引標籤。  按一下 \[增益集\] 索引標籤上的 \[插入文字\] 及 \[插入表格\] 按鈕來測試程式碼。  
  
#### 測試 VSTO 增益集  
  
1.  請按 F5 執行您的專案。  
  
2.  確認功能區上顯示有 \[增益集\] 索引標籤。  
  
3.  按一下 \[增益集\] 索引標籤。  
  
4.  確認功能區上顯示有 \[內容\] 群組。  
  
5.  按一下 \[內容\] 群組中的 \[插入文字\] 按鈕。  
  
     這會在文件目前的游標位置上加入字串。  
  
6.  按一下 \[內容\] 群組中的 \[插入表格\] 按鈕。  
  
     這會在文件目前的游標位置上加入表格。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：  
  
-   自訂不同 Office 應用程式的功能區。  如需支援自訂功能區之應用程式的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
-   使用功能區設計工具自訂 Office 應用程式的功能區。  如需詳細資訊，請參閱[功能區設計工具](../vsto/ribbon-designer.md)。  
  
-   建立自訂執行窗格。  如需詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
-   使用 Outlook 表單區域自訂 Microsoft Office Outlook 的 UI。  如需詳細資訊，請參閱[逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  