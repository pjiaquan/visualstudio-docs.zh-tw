---
title: "逐步解說：將 XML 資料讀入資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 從 XML 檔案讀取"
  - "資料存取 [Visual Studio], XML 資料"
  - "資料集 [Visual Basic], 讀取 XML 資料"
  - "讀取資料, XML 檔案"
  - "讀取檔案, XML"
  - "讀取 XML"
  - "XML [Visual Studio], 讀取"
  - "XML 文件, 讀取"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將 XML 資料讀入資料集
ADO.NET 提供簡單的方法來使用 XML 資料。  在這份逐步解說中，您將建立 Windows 應用程式，來將 XML 資料載入資料集。  接著資料集就會顯示在 <xref:System.Windows.Forms.DataGridView> 中。  最後，根據 XML 檔內容建立的 XML 結構描述將會顯示在文字方塊中。  
  
 此逐步解說包含五個主要的步驟：  
  
1.  建立新專案。  
  
2.  建立要讀入資料集的 XML 檔案。  
  
3.  建立使用者介面。  
  
4.  建立資料集、讀取 XML 檔，並將其顯示在 <xref:System.Windows.Forms.DataGridView> 控制項中。  
  
5.  加入程式碼，在 <xref:System.Windows.Forms.TextBox> 控制項中顯示以 XML 檔為基礎的 XML 結構描述。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立新專案  
 在這個步驟中，您將建立包含這份逐步解說的 Visual Basic 或 Visual C\# 專案。  
  
#### 若要建立新的 Windows 專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 `ReadingXML`。  
  
3.  選取 \[**Windows 應用程式**\]，並按一下 \[**確定**\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     \[**ReadingXML**\] 專案隨即建立並加入至 \[方案總管\]。  
  
## 產生要讀入資料集的 XML 檔  
 由於這份逐步解說主要是將 XML 資料讀入資料集，因此會提供 XML 檔的內容。  
  
#### 若要建立要讀入資料集的 XML 檔案  
  
1.  從 \[**專案**\] 功能表選擇 \[**加入新項目**\]。  
  
2.  選取 \[**XML 檔**\]，將檔案命名為 `authors.xml`，再按一下 \[**加入**\]。  
  
     XML 檔案會載入至設計工具中，並且可以開始編輯。  
  
3.  將以下程式碼貼入編輯器中 XML 宣告的下方：  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  在 \[**檔案**\] 功能表中，指向 \[**儲存 authors.xml**\]。  
  
## 建立使用者介面  
 這個應用程式的使用者介面將包含：  
  
-   將 XML 檔的內容當做資料顯示的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   針對 XML 檔顯示 XML 結構描述的 <xref:System.Windows.Forms.TextBox> 控制項。  
  
-   兩個 <xref:System.Windows.Forms.Button> 控制項。  
  
    -   一個按鈕會將 XML 檔讀入資料集，並將其顯示在 <xref:System.Windows.Forms.DataGridView> 控制項中。  
  
    -   第二個按鈕會從資料集擷取結構描述，並透過 <xref:System.IO.StringWriter> 將其顯示在 <xref:System.Windows.Forms.TextBox> 控制項中。  
  
#### 若要將控制項加入至表單  
  
1.  在設計檢視中開啟 `Form1`。  
  
2.  從 \[**工具箱**\] 中，將下列控制項拖曳到表單上：  
  
    -   一個 <xref:System.Windows.Forms.DataGridView> 控制項  
  
    -   一個 <xref:System.Windows.Forms.TextBox> 控制項  
  
    -   兩個 <xref:System.Windows.Forms.Button> 控制項  
  
3.  設定下列屬性：  
  
    |控制項|屬性|設定|  
    |---------|--------|--------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**垂直**|  
    |`Button1`|**名稱**|`ReadXmlButton`|  
    ||**文字**|`Read XML`|  
    |`Button2`|**名稱**|`ShowSchemaButton`|  
    ||**文字**|`Show Schema`|  
  
## 建立接收 XML 資料的資料集  
 在下一個程序中，您會建立名為 `authors` 的新資料集。  如需資料集的詳細資訊，請參閱 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
#### 若要建立將接收 XML 資料的新資料集  
  
1.  當 \[**方案總管**\] 中選取了 \[**Form1**\] 的原始程式檔時，請按一下 \[**方案總管**\] 工具列中的 \[**設計工具檢視**\] 按鈕。  
  
2.  從[資料索引標籤、工具箱](../ide/reference/toolbox-data-tab.md)，將 \[**資料集**\] 拖曳至 \[**Form1**\]。  
  
3.  選取 **不具型別資料集** 的 **加入資料集** 對話方塊中，然後按一下 **確定**。  
  
     \[**DataSet1**\] 隨即加入元件匣中。  
  
4.  請在 \[**屬性**\] 視窗中，將 \[**Name**\] 和 <xref:System.Data.DataSet.DataSetName%2A> 屬性設定為 `AuthorsDataSet`。  
  
## 建立將 XML 讀入資料集的事件處理常式  
 \[**Read XML**\] 按鈕會將 XML 檔讀入資料集中，並在 <xref:System.Windows.Forms.DataGridView> 控制項上設定繫結至此資料集的屬性。  
  
#### 若要將程式碼加入至 ReadXmlButton\_Click 事件處理常式  
  
1.  在 \[**方案總管**\] 中，選取 \[**Form1**\]，並按一下 \[**方案總管**\] 工具列上的 \[**設計工具檢視**\] 按鈕。  
  
2.  按兩下 \[**Read XML**\] 按鈕。  
  
     \[**程式碼編輯器**\] 會在 `ReadXmlButton_Click` 事件處理常式上開啟。  
  
3.  將下列程式碼輸入到 `ReadXmlButton_Click` 事件處理常式：  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  在 `ReadXMLButton_Click` 事件處理常式程式碼中，將 `filepath =` 項目變更為正確路徑。  
  
## 建立在文字方塊中顯示結構描述的事件處理常式  
 \[**Show Schema**\] 按鈕會建立 <xref:System.IO.StringWriter> 物件，此物件中已填入此結構描述，並顯示在 <xref:System.Windows.Forms.TextBox> 中。  
  
#### 若要將程式碼加入至 ShowSchemaButton\_Click 事件處理常式  
  
1.  從 \[**方案總管**\] 中選取 \[**Form1**\]，再按一下 \[**設計工具檢視**\] 按鈕。  
  
2.  按兩下 \[**Show Schema**\] 按鈕。  
  
     \[**程式碼編輯器**\] 會在 `ShowSchemaButton_Click` 事件處理常式上開啟。  
  
3.  將下列程式碼輸入到 `ShowSchemaButton_Click` 事件處理常式。  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## 測試  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
1.  按下 F5 執行應用程式。  
  
2.  按一下 \[**Read XML**\] 按鈕。  
  
     DataGridView 會顯示 XML 檔案的內容。  
  
3.  按一下 \[**Show Schema**\] 按鈕。  
  
     文字方塊會顯示 XML 檔案的 XML 結構描述。  
  
## 後續步驟  
 這個逐步解說會說明將 XML 檔案讀入資料集，以及依據 XML 檔案內容建立結構描述的基本操作方法。  以下則是接下來的一些工作：  
  
-   編輯資料集中的資料並將其寫出為 XML。  如需詳細資訊，請參閱 <xref:System.Data.DataSet.WriteXml%2A>。  
  
-   編輯資料集中的資料並將其寫出至資料庫。  如需詳細資訊，請參閱[儲存資料](../data-tools/saving-data.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)