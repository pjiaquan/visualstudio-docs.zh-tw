---
title: "逐步解說：將應用程式頁面新增到工作流程 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 將應用程式頁面加入至工作流程"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 逐步解說：將應用程式頁面新增到工作流程
  本逐步解說示範如何將應用程式頁面加入至工作流程專案，此應用程式頁面會顯示衍生自工作流程的資料。  本逐步解說以[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主題所述的專案為基礎。  
  
 本逐步解說將示範下列工作：  
  
-   將 ASPX 應用程式頁面加入至 SharePoint 工作流程專案。  
  
-   從工作流程專案取得並操作資料。  
  
-   在應用程式頁面上的表格中顯示資料。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   您也必須完成[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主題中的專案。  
  
## 修改工作流程程式碼  
 首先，將一行程式碼加入至工作流程，將 \[結果\] 欄的值設定為費用報表的金額。  此值稍後會用於費用報表摘要計算。  
  
#### 若要設定工作流程中的結果欄值  
  
1.  將[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)主題完成的專案載入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  開啟 Workflow1.cs 或 Workflow1.vb 的程式碼 \(視您的程式語言而定\)。  
  
3.  在 `createTask1_MethodInvoking` 方法的底部加入下列程式碼：  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## 建立應用程式頁面  
 接下來，將 ASPX 表單加入至專案。  此表單將顯示從費用報表工作流程專案取得的資料。  若要這麼做，您將加入應用程式頁面。  應用程式頁面使用的主版頁面與其他 SharePoint 頁面相同，表示它會與 SharePoint 網站上的其他頁面相似。  
  
#### 若要將應用程式頁面加入至專案  
  
1.  選取 ExpenseReport 專案，然後在功能表列上，選擇 \[**專案**\]、 \[**加入新項目**\]。  
  
2.  在 \[**範本**\] 窗格中，選取 \[**應用程式頁面**\] 範本，為專案項目 \(**ApplicaitonPage1.aspx**\) 使用預設名稱，然後選擇 \[**加入**\] 按鈕。  
  
3.  在 ApplicationPage1.aspx 的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 中，以下列程式碼取代 `PlaceHolderMain` 區段：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     此程式碼會將表格以及標題加入至頁面。  
  
4.  以下列程式碼取代 `PlaceHolderPageTitleInTitleArea` 區段，將標題加入至應用程式頁面：  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## 撰寫應用程式頁面的程式碼  
 接下來，將程式碼加入至費用報表摘要應用程式頁面。  當您開啟頁面時，程式碼會掃描 SharePoint 中的工作清單，找出超過所配置支出限制的費用。  報表會列出每個項目以及費用總和。  
  
#### 若要撰寫應用程式頁面的程式碼  
  
1.  選擇 \[**ApplicationPage1.aspx**\] 節點，然後在功能表列上選擇 \[**檢視**\]、\[**程式碼**\]，顯示應用程式頁面的後置程式碼。  
  
2.  以下列程式碼取代類別最上方的 **using** 或 **Import** 陳述式 \(視您的程式語言而定\)：  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  將下列程式碼加入至 `Page_Load` 方法中：  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  請務必以正在執行 SharePoint 的有效伺服器名稱取代「TestServer」中的程式碼。  
  
## 測試應用程式頁面  
 接下來，判斷應用程式頁面是否正確顯示費用資料。  
  
#### 若要測試應用程式頁面  
  
1.  按 F5 鍵執行並部署專案至 SharePoint。  
  
2.  選擇 \[**首頁**\] 按鈕，然後選擇快速啟動列上的 \[**共用文件**\] 連結，以顯示 SharePoint 網站上的 \[共用文件\] 清單。  
  
3.  若要呈現此範例的費用報表，請在頁面頂端選擇 \[**程式庫工具**\] 索引標籤上的 \[**文件**\] 連結，將一些新文件上載至 \[文件\] 清單，然後選擇工具功能區上的 \[**上載文件**\] 按鈕。  
  
4.  在您上載某些檔案後，請選取在 \[**LibraryTools**\] 索引標籤上的 \[**程式庫**\] 連結頁面的頂端然後選取工具功能區上的 \[**程式庫設定**\] 按鈕，進行具現化工作流程。  
  
5.  在 \[**文件庫設定**\] 頁面上，選擇 \[**權限與管理**\] 區段中的 \[**工作流程設定**\] 連結。  
  
6.  選擇 \[**工作流程設定**\] 頁面中的 \[**加入工作流程**\] 連結。  
  
7.  在 \[**加入工作流程**\] 頁面中，選取 \[**ExpenseReport \- Workflow1**\] 工作流程，輸入工作流程的名稱，例如 ExpenseTest，然後按 \[**下一步**\] 按鈕。  
  
     工作流程關聯表單隨即出現。  使用此表單來報告費用限制金額。  
  
8.  在關聯表單，請輸入 **1000** 至 \[**自動核准限制**\] 方塊中，然後選擇 \[**關聯的工作流程**\] 按鈕。  
  
9. 按 \[**首頁**\] 按鈕回到 SharePoint 首頁。  
  
10. 按一下快速啟動列上的 \[**共用文件**\] 連結。  
  
11. 選取其中一個上載的文件來顯示下拉箭號，選取它，然後選取 \[**工作流程**\] 項目。  
  
12. 按一下 ExpenseTest 旁的影像，以顯示工作流程初始表單。  
  
13. 在 \[**總支出**\] 文字方塊中輸入大於 1000 的值，然後按一下 \[**啟動工作流程**\] 按鈕。  
  
     當報告的費用超過所配置的費用金額時，會將工作加入至工作清單。  名為 \[**ExpenseTest**\] 的欄和值 \[**已完成**\] 也會加入至 \[共用文件\] 清單中的費用報表項目。  
  
14. 針對 \[共用文件\] 清單中的其他文件重複步驟 11 \- 13\(文件的精確數字並不重要\)。  
  
15. 在 Web 瀏覽器中開啟下列 URL，顯示費用報表摘要應用程式頁面：**http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**。  
  
     費用報表摘要頁面會顯示超過所配置金額的所有費用報表、超過的金額，以及所有報表的總金額。  
  
## 後續步驟  
 如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 您可以透過下列主題，進一步了解如何使用 Visual Studio 中的 Visual Web 設計工具來設計 SharePoint 頁面內容：  
  
-   [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 請參閱  
 [逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)   
 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  