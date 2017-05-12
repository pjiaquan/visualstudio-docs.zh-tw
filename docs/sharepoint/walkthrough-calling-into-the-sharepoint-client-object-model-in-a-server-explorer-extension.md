---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  本逐步解說將示範如何從 \[**伺服器總管**\] 中 \[**SharePoint 連接**\] 節點的擴充功能呼叫 SharePoint 用戶端物件模型。  如需如何使用 SharePoint 用戶端物件模型的詳細資訊，請參閱 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能，該擴充功能會透過下列方式擴充 \[**伺服器總管**\] 的 \[**SharePoint 連接**\] 節點：  
  
    -   副檔名將 \[**Web 組件庫**\] 位於 \[**伺服器總管**\] 的每個 SharePoint 網站節點下。  這個新節點包含的子節點代表網站上 Web 組件庫中的每一個 Web 組件。  
  
    -   副檔名會定義代表 Web 組件執行個體的新節點類型。  這個新節點類型是新的 \[**Web 組件庫**\] 節點底下子節點的基礎。  新的 Web 組件節點類型會在 \[**屬性**\] 視窗中有關這個節點表示的 Web 組件。  
  
-   建置 Visual Studio Extension \(VSIX\) Package 以部署擴充功能。  
  
-   偵錯和測試擴充功能。  
  
> [!NOTE]  
>  在這個逐步解說中建立的擴充功能類似於您在 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)建立的擴充功能。  逐步解說會使用 SharePoint 伺服器物件模型，不過，本逐步解說使用用戶端物件模型，完成相同的工作。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本逐步解說使用 SDK 中的 \[**VSIX 專案**\] 範本建立 VSIX 套件，以部署擴充功能。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   使用 SharePoint 用戶端物件模型。  如需詳細資訊，請參閱 [Managed 用戶端物件模型](http://go.microsoft.com/fwlink/?LinkId=177797) \(英文\)。  
  
-   在 SharePoint 的 Web 組件。  如需詳細資訊，請參閱 [Web 組件概觀](http://go.microsoft.com/fwlink/?LinkId=177803) \(英文\)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立兩個專案：  
  
-   VSIX 專案會建立 VSIX 套件以部署 \[**伺服器總管**\] 副檔名。  
  
-   類別庫專案實作 \[**伺服器總管**\] 副檔名。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**擴充性**\]。  
  
    > [!NOTE]  
    >  為，當您安裝 Visual Studio SDK， \[**擴充性**\] 有節點的。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
4.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
     SharePoint 工具擴充功能需要這個 .NET Framework 版本的功能。  
  
5.  選取 \[**VSIX 專案**\] 範本。  
  
6.  在 \[**Name**\] 方塊中，輸入 **其中**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**WebPartNode**\] 專案加入至 \[**方案總管**\]。  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\]，開啟方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[ **新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**視窗**\]。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
4.  在專案範本清單中，選取 \[**類別庫**\]。  
  
5.  在 \[**Name**\]方塊中，輸入 **WebPartNodeExtension**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**WebPartNodeExtension**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
6.  從專案刪除 Class1 程式碼檔。  
  
## 設定擴充功能專案  
 在您撰寫程式碼建立擴充功能之前，您必須將程式碼檔案和組件參考加入至您的專案，因此，您必須更新預設命名空間。  
  
#### 若要設定專案  
  
1.  在 \[**WebPartNodeExtension**\]專案中，加入名為和的兩個 WebPartNodeTypeProvider SiteNodeExtension 程式碼檔。  
  
2.  開啟 WebPartNodeExtension 專案的捷徑功能表，然後選取 \[**新增參考**\]。  
  
3.  在 **參考管理員– WebPartNodeExtension** 對話方塊中，選取 \[**Framework**\] 節點，針對 System.ComponentModel.Composition 和 System.Windows.Forms 組件然後選取核取方塊。  
  
4.  選取 \[**延伸**\] 節點，為下列組件中選取核取方塊，然後選取 \[**確定**\] 按鈕:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  開啟 \[**WebPartNodeExtension**\]專案的捷徑功能表，然後選取 \[**屬性**\]。  
  
     \[**專案設計工具**\] 隨即開啟。  
  
6.  選取 \[**應用程式**\] 索引標籤。  
  
7.  在方塊中 \[**預設命名空間**\] \(C\#\) 或 \[**根命名空間**\] 方塊 \(Visual Basic\)，輸入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
## 建立新節點的圖示  
 建立 \[**伺服器總管**\] 副檔名的兩個圖示:新的 \[**Web 組件庫**\] 節點的圖示和每個子網路的另一個圖示個別節點在 \[**Web 組件庫**\] 節點下。  稍後在本逐步解說中，您將撰寫使這些圖示與節點的程式碼。  
  
#### 若要建立節點的圖示  
  
1.  在 WebPartNodeExtension 專案中的 \[**專案設計工具**\] ，選取 \[**資源**\] 索引標籤。  
  
2.  選取這個專案不包含預設資源檔的連結 \[**。請按這裡建立資源檔。**\]  
  
     Visual Studio 會建立資源檔並在編輯器中開啟設計工具。  
  
3.  在設計工具頂端，選取\[**加入資源**\] 功能表命令的箭號，然後選取 \[**加入新圖示。**\]。  
  
4.  輸入新圖示的名稱 **WebPartsNode** ，然後選取 \[**新增**\] 按鈕。  
  
     新圖示隨即開啟於 \[**影像編輯器**\] 中。  
  
5.  編輯 16x16 版的圖示，以便能夠輕易地辨識其設計。  
  
6.  開啟 32x32 版的圖示的捷徑功能表，然後選取 \[**刪除影像類型**\]。  
  
7.  迴圈將第二個圖示的第三個步驟至第大小圖示加入至專案資源，並命名為圖示 **WebPart**。  
  
8.  在 \[**方案總管**\]，在 \[**WebPartNodeExtension**\]專案的 \[**資源**\] 資料夾，選取 \[**WebPartsNode.ico**\]。  
  
9. 在 \[**屬性**\] 視窗，請開啟 \[**建置動作**\] 清單，然後選取 \[**內嵌資源**\]。  
  
10. 針對 **WebPart.ico** 重複最後兩個步驟。  
  
## 將 Web 組件庫節點加入至伺服器總管  
 建立一個將新的 \[**Web 組件庫**\] 節點加入至每個 SharePoint 網站節點的類別。  為了加入新節點，此類別會實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面。  在您要擴充 \[**伺服器總管**\] 中現有節點的行為時實作此介面，例如將新的子節點加入至節點。  
  
#### 若要將 Web 組件庫節點加入至伺服器總管  
  
1.  下列程式碼貼入 \[**WebPartNodeExtension**\]專案的 \[**SiteNodeExtension**\]程式碼檔案。  
  
    > [!NOTE]  
    >  加入這個程式碼之後，專案會出現一些編譯錯誤。  在後續步驟中加入程式碼時，這些錯誤將不存在。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## 定義代表 Web 組件的節點類型  
 建立類別，該類別會定義代表 Web 組件的新節點類型。  Visual Studio 會使用這個新節點類型顯示子節點 \[**Web 組件庫**\] 節點下。  這些子節點每一個都代表 SharePoint 網站上的單一 Web 組件。  
  
 為了定義新的節點類型，此類別會實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面。  在您要於 \[**伺服器總管**\] 中定義新的節點類型時實作此介面。  
  
#### 若要定義 Web 組件節點類型  
  
1.  下列程式碼貼入 \[**WebPartNodeExtension**\]專案的 \[**WebPartNodeTypeProvider**\]程式碼檔案。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## 檢查點  
 進行到逐步解說中的這個步驟時，\[**Web 組件庫**\] 節點的所有程式碼現在都會位於專案中。  建立 \[**WebPartNodeExtension**\]專案，以確定專案在編譯時未發生任何錯誤。  
  
#### 若要建置專案  
  
1.  在 \[**方案總管**\]，開啟 \[**WebPartNodeExtension**\]專案的捷徑功能表，然後選取 \[**組建**\]。  
  
## 建立 VSIX 套件以部署擴充功能  
 若要部署擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改專案包含的 source.extension.vsixmanifest 檔案來設定 VSIX 套件。  然後您可以建置方案建立 VSIX 套件。  
  
#### 若要設定 VSIX 套件  
  
1.  在 \[**方案總管**\]，在 \[**其中**\] 專案，在資訊清單編輯器中開啟 \[**source.extension.vsixmanifest**\]檔案。  
  
     source.extension.vsixmanifest 檔案是所有 VSIX 套件所需要的 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**產品名稱**\]方塊中，輸入 **Web 組件伺服器總管的庫節點**。  
  
3.  在 \[**作者**\]方塊中，輸入 **Contoso**。  
  
4.  在 \[**Description**\]方塊中，輸入 **將自訂 Web 組件庫節點加入至伺服器總管的 SharePoint 連接節點**。  
  
5.  在編輯器中 \[**資產**\] 索引標籤上，選取 \[**新增**\] 按鈕。  
  
6.  在 \[**將新的屬性**\] 對話方塊，在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
8.  在 \[**Project**\] 清單中，選取 \[**WebPartNodeExtension**\]，然後選取 \[**確定**\] 按鈕。  
  
9. 在功能表列上，選擇， \[**組建**\]\[**建置方案**\]，然後確定方案編譯時未發生任何錯誤。  
  
10. 確定 WebPartNode 專案的建置輸出資料夾現已包含 WebPartNode.vsix 檔。  
  
     根據預設，建置輸出資料夾為 ..  \\bin\\Debug 資料夾，其位於專案檔案包含的資料夾下。  
  
## 測試擴充功能  
 現在您可以測試 \[**伺服器總管**\] 中新的 \[**Web 組件庫**\] 節點。  首先，偵錯在 Visual Studio 的實驗執行個體中擴充專案開始。  然後使用新的 \[**Web 組件**\] 節點在 Visual Studio 的實驗執行個體。  
  
#### 若要啟動對擴充功能的偵錯  
  
1.  重新啟動以管理認證的 Visual Studio，然後開啟 \[**其中**\] 方案。  
  
2.  在 WebPartNodeExtension 專案中，開啟 **SiteNodeExtension** 程式碼檔，然後將中斷點加入至 `NodeChildrenRequested` 和 `CreateWebPartNodes` 方法的第一行程式碼。  
  
3.  選擇 F5 鍵開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile% \\ AppData \\ Local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ Extensions \\ Contoso \\ Web 組件庫節點擴充伺服器總管的\\模糊並啟動 Visual Studio 的實驗執行個體。  您在這個執行個體中測試專案項目 Visual Studio。  
  
#### 若要測試擴充功能  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇 \[**檢視**\]， \[**伺服器總管**\]。  
  
2.  確認要用來進行測試的 SharePoint 網站出現在 \[**伺服器總管**\] 中的 \[**SharePoint 連接**\] 節點底下。  如果未列出，請執行下列步驟:  
  
    1.  開啟 \[**SharePoint 連接**\] 的捷徑功能表，然後選取 \[**加入連結**\]。  
  
    2.  在 \[**加入 SharePoint 連接**\] 對話方塊中，輸入要連接的 SharePoint 網站的 URL，然後選擇 \[**確定**\] 按鈕。  
  
         若要指定開發電腦上的 SharePoint 網站，請輸入 **http:\/\/localhost**。  
  
3.  展開以顯示網站 URL 的網站連接節點 \(，然後展開子網站節點 \(例如， \[**合作網站**\]\)。  
  
4.  確認在另一個 Visual Studio 執行個體中的程式碼在您之前於方法 `NodeChildrenRequested` ，然後選擇 F5 鍵繼續偵錯專案的中斷點停止。  
  
5.  在 Visual Studio 的實驗執行個體中，展開 \[**Web 組件庫**\] 節點，會出現在最上層網站節點下。  
  
6.  確認在另一個 Visual Studio 執行個體中的程式碼在您之前於方法 `CreateWebPartNodes` ，然後選擇 F5 鍵繼續偵錯專案的中斷點停止。  
  
7.  在 Visual Studio 的實驗執行個體中，確認所連接網站上的所有 Web 組件都出現在 \[**伺服器總管**\] 中的 \[**Web 組件庫**\] 節點底下。  
  
8.  開啟 Web 組件的捷徑功能表，然後選取 \[**屬性**\]。  
  
9. 在 \[**屬性**\] 視窗，請確認關於 Web 組件的詳細資料隨即出現。  
  
10. 在 \[**伺服器總管**\]，開啟相同 Web 組件的捷徑功能表，然後選取 \[**顯示訊息。**\]。  
  
     在隨即出現的訊息方塊中，選取 \[**確定**\] 按鈕。  
  
## 從 Visual Studio 解除安裝擴充功能  
 在您完成測試擴充功能之後，解除安裝它從 Visual Studio。  
  
#### 若要解除安裝擴充功能  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇， \[**工具**\]\[**副檔名和更新**\]。  
  
     \[**副檔名和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選取 **Web 組件伺服器總管的庫節點**，然後選取 \[**解除安裝**\] 按鈕。  
  
3.  在出現的對話方塊中，選取 \[**是**\] 按鈕。  
  
4.  選取 \[**立即重新啟動**\] 按鈕完成解除安裝。  
  
     專案項目也會解除安裝。  
  
5.  關閉 Visual Studio 的實驗執行個體和 WebPartNode 方案已開啟\) 的兩個執行個體執行 Visual Studio。  
  
## 請參閱  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  