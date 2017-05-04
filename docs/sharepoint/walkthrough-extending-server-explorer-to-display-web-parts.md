---
title: "Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  在 Visual Studio 中，您可以使用 \[**伺服器總管**\]\[**SharePoint 連接**\] 節點來檢視在 SharePoint 網站的元件。  然而，預設 \[**伺服器總管**\] 不顯示某些元件。  在這個逐步解說中，您將擴充 \[**伺服器總管**\] ，讓它顯示在每個連接的 SharePoint 網站的 Web 組件庫。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能，該擴充功能會透過下列方式擴充 \[**伺服器總管**\]：  
  
    -   副檔名將 \[**Web 組件庫**\] 位於 \[**伺服器總管**\] 的每個 SharePoint 網站節點下。  這個新節點包含的子節點代表網站上 Web 組件庫中的每一個 Web 組件。  
  
    -   副檔名會定義代表 Web 組件執行個體的新節點類型。  這個新節點類型是新的 \[**Web 組件庫**\] 節點底下子節點的基礎。  新的 Web 組件節點類型會在 \[**屬性**\] 視窗中，顯示所代表 Web 組件的相關資訊。  節點型別也包括可用來做為起點為執行其他工作與 Web 組件相關的自訂捷徑功能表項目。  
  
-   建立擴充組件呼叫的兩個自訂 SharePoint 命令。  SharePoint 命令是在伺服器物件模型可以由擴充組件呼叫使用 SharePoint API 為的方法。  在本逐步解說中，您將會建立命令，在開發電腦上擷取本機 SharePoint 網站中的 Web 組件資訊。  如需詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   建置 Visual Studio Extension \(VSIX\) Package 以部署擴充功能。  
  
-   偵錯和測試擴充功能。  
  
> [!NOTE]  
>  如需使用 SharePoint 用戶端物件模型而非伺服器物件模型本逐步解說的替代版本，請參閱 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   使用的 SharePoint 伺服器物件模型。  如需詳細資訊，請參閱[使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796) \(英文\)。  
  
-   SharePoint 方案中的 Web 組件。  如需詳細資訊，請參閱 [Web 組件概觀](http://go.microsoft.com/fwlink/?LinkId=177803) \(英文\)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立三個專案:  
  
-   VSIX 專案，用於建立 VSIX 套件以部署擴充功能。  
  
-   類別庫專案，可實作擴充功能。  這個專案必須以 .NET Framework 4.5。  
  
-   類別庫專案，可定義自訂 SharePoint 命令。  這個專案必須以 .NET Framework 3.5 為目標。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
3.  在 \[ **新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**擴充性**\] 節點。  
  
    > [!NOTE]  
    >  為，當您安裝 Visual Studio SDK， \[**擴充性**\] 有節點的。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
4.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
5.  選取 \[**VSIX 專案**\] 範本，將專案命名為 **其中**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**WebPartNode**\] 專案加入至 \[**方案總管**\]。  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\]，開啟方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\]節點，然後選取 \[**視窗**\] 節點。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
4.  在專案範本清單中，選取， \[**類別庫**\] 命名 **WebPartNodeExtension**專案，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**WebPartNodeExtension**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
#### 若要建立 SharePoint 命令專案  
  
1.  在 \[**方案總管**\]，開啟方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[ **新增專案**\]  對話方塊中，展開 **Visual C\#** 節點或 \[**Visual Basic**\]節點，然後選取 \[**視窗**\] 節點。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 3.5**\] 。  
  
4.  在專案範本清單中，選取 \[**類別庫**\]，名為 **WebPartCommands**專案，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**WebPartCommands**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定專案  
 在您撰寫程式碼建立擴充功能之前，您必須將程式碼檔案和組件參考，並且設定專案設定。  
  
#### 若要設定 WebPartNodeExtension 專案  
  
1.  在 WebPartNodeExtension 專案中，加入名稱如下的四個程式碼檔:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  開啟 \[**WebPartNodeExtension**\]專案的捷徑功能表，然後選取 \[**新增參考**\]。  
  
3.  在 **參考管理員– WebPartNodeExtension** 對話方塊中，選取 \[**Framework**\] 索引標籤，為下列組件都然後選取核取方塊:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  選取 \[**延伸**\] 索引標籤，為 Microsoft.VisualStudio.SharePoint 組件選取核取方塊，然後選取 \[**確定**\] 按鈕。  
  
5.  在 \[**方案總管**\]，開啟 \[**WebPartNodeExtension**\]專案節點的捷徑功能表，然後選取 \[**屬性**\]。  
  
     \[**專案設計工具**\] 隨即開啟。  
  
6.  選取 \[**應用程式**\] 索引標籤。  
  
7.  在方塊中 \[**預設命名空間**\] \(C\#\) 或 \[**根命名空間**\] 方塊 \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\)，輸入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
#### 若要設定 WebPartCommands 專案  
  
1.  在 \[WebPartCommands\] 專案中，加入名為 WebPartCommands 的程式碼檔。  
  
2.  在 \[**方案總管**\]，開啟 \[**WebPartCommands**\]專案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**現有項目**\]。  
  
3.  在 \[**新增現有項目**\] 對話方塊中，瀏覽至包含 WebPartNodeExtension 專案的程式碼檔的資料夾，然後選取 WebPartNodeInfo 和 WebPartCommandIds 程式碼檔案。  
  
4.  在 \[**新增**\] 按鈕選取旁邊的箭號，然後選取時出現的功能表的 \[**加入做為連結**\] 。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將程式碼檔加入至 WebPartCommands 專案做為連結。  因此，程式碼檔案在 WebPartNodeExtension 專案中，，但是檔案中的程式碼在 \[WebPartCommands\] 專案也會編譯。  
  
5.  再次開啟 \[**WebPartCommands**\]專案的捷徑功能表，然後選擇\[**新增參考**\]。  
  
6.  在 **參考管理員– WebPartCommands** 對話方塊中，選取 \[**延伸**\] 索引標籤，為下列組件中選取核取方塊，然後選取 \[**確定**\] 按鈕:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  在 \[**方案總管**\]，再開啟 \[**WebPartCommands**\]專案的捷徑功能表，然後選取 \[**屬性**\]。  
  
     \[**專案設計工具**\] 隨即開啟。  
  
8.  選取 \[ **應用程式**\] 索引標籤。  
  
9. 在方塊中 \[**預設命名空間**\] \(C\#\) 或 \[**根命名空間**\] 方塊 \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\)，輸入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
## 建立新節點的圖示  
 為 \[**伺服器總管**\] 擴充功能建立兩個圖示：一個圖示用於新的 \[**Web 組件庫**\] 節點，另一個圖示用於 \[**Web 組件庫**\] 節點底下的每個 Web 組件子節點。  稍後在本逐步解說中，您將寫入讓這些圖示與節點產生關聯的程式碼。  
  
#### 若要建立節點的圖示  
  
1.  在 \[**方案總管**\]，開啟 \[**WebPartNodeExtension**\]專案的捷徑功能表，然後選取 \[**屬性**\]。  
  
2.  \[**專案設計工具**\] 隨即開啟。  
  
3.  選取 \[**資源**\] 索引標籤，然後 \[**選取此專案只包含預設資源檔。請按這裡建立一**\] 個連結。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立資源檔並在編輯器中開啟設計工具。  
  
4.  在設計工具頂端，請在 \[**加入資源**\] 功能表命令選取旁邊的箭號，然後選取時出現的功能表的 \[**加入新圖示。**\] 。  
  
5.  在 \[**加入新資源**\] 對話方塊中，為新的 **WebPartsNode**圖示，然後選取 \[**新增**\] 按鈕。  
  
     新圖示隨即開啟於 \[**影像編輯器**\] 中。  
  
6.  編輯 16x16 版的圖示，以便能夠輕易地辨識其設計。  
  
7.  開啟 32x32 版的圖示的捷徑功能表，然後選取 \[**刪除影像類型**\]。  
  
8.  迴圈將第二個圖示的第五個步驟至第、圖示加入至專案資源，並命名為圖示 **WebPart**。  
  
9. 在 \[**方案總管**\]，在 \[**WebPartNodeExtension**\]專案的 \[**資源**\] 資料夾中，開啟 \[**WebPartsNode.ico**\] 的捷徑功能表。  
  
10. 在 \[**屬性**\] 視窗，請在 \[**建置動作**\] 選取旁邊的箭號，然後選取時出現的功能表的 \[**內嵌資源**\] 。  
  
11. 針對 **WebPart.ico** 重複最後兩個步驟。  
  
## 將 Web 組件庫節點加入至伺服器總管  
 建立一個將新的 \[**Web 組件庫**\] 節點加入至每個 SharePoint 網站節點的類別。  為了加入新節點，此類別會實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面。  實作這個介面，每當您要擴充現有節點的行為在 \[**伺服器總管**\] 的，例如將子節點加入至節點。  
  
#### 若要將 Web 組件庫節點加入至伺服器總管  
  
1.  在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔，然後將下列程式碼貼入其中。  
  
    > [!NOTE]  
    >  加入這個程式碼之後，專案會出現一些編譯錯誤，不過，它們會消失，當您將在稍後的步驟中的程式碼。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## 定義代表 Web 組件的節點類型  
 建立類別，該類別會定義代表 Web 組件的新節點類型。  Visual Studio 會使用這個新節點類型顯示子節點 \[**Web 組件庫**\] 節點下。  每個子節點表示 SharePoint 網站的 Web 組件。  
  
 為了定義新的節點類型，此類別會實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面。  在您要於 \[**伺服器總管**\] 中定義新的節點類型時實作此介面。  
  
#### 若要定義 Web 組件節點類型  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartNodeTypeProvder 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## 定義 Web 組件資料類別  
 定義包含 SharePoint 網站上單一 Web 組件相關資料的類別。  稍後在本逐步解說中，您將建立類別擷取有關每個 Web 組件資料在整個網站並將資料儲存到這個類別執行個體的自訂 SharePoint 命令。  
  
#### 若要定義 Web 組件資料類別  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartNodeInfo 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## 定義 SharePoint 命令的識別碼  
 定義數個指定自訂 SharePoint 命令的字串。  稍後您將在本逐步解說中實作這些命令。  
  
#### 若要定義命令識別碼  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartCommandIds 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## 建立自訂 SharePoint 命令  
 建立的呼叫 SharePoint 伺服器物件模型中擷取有關 Web 組件資料 SharePoint 網站的自訂命令。  每個命令都是已套用 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 的方法。  
  
#### 若要定義 SharePoint 命令  
  
1.  在 \[WebPartCommands\] 專案中，開啟 WebPartCommands 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## 檢查點  
 進行到逐步解說中的這個步驟時，\[**Web 組件庫**\] 節點的所有程式碼和 SharePoint 命令都會位於專案中。  建置解決方案，以確定這兩個專案在編譯時未發生任何錯誤。  
  
#### 若要建置方案  
  
1.  在功能表列上，選擇， \[**組建**\]\[**建置方案**\]。  
  
    > [!WARNING]  
    >  此時，，因為 VSIX 資訊清單檔沒有的作者，值 WebPartNode 專案可能會發生建置錯誤。  當您將在稍後的步驟中，這個值表示此錯誤就會消失。  
  
## 建立 VSIX 套件以部署擴充功能  
 若要部署擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案中的 source.extension.vsixmanifest 檔案來設定 VSIX 套件。  接著，建置方案來建立 VSIX 套件。  
  
#### 若要設定 VSIX 套件  
  
1.  在 \[**方案總管**\]，於 WebPartNode 專案中，開啟在資訊清單編輯器中 \[**source.extension.vsixmanifest**\]檔案。  
  
     source.extension.vsixmanifest 檔案是所有 VSIX 套件所需要的 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**產品名稱**\]方塊中，輸入 **Web 組件伺服器總管的庫節點**。  
  
3.  在 \[**作者**\]方塊中，輸入 **Contoso**。  
  
4.  在 \[**描述**\] 方塊中，**輸入將自訂 Web 組件庫節點加入至伺服器總管的 SharePoint 連接節點。此擴充使用自訂 SharePoint 命令呼叫伺服器物件模型。**  
  
5.  選取編輯器的 \[**資產**\] 索引標籤，然後選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
6.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
8.  在 \[**Project**\] 清單中，選取 \[**WebPartNodeExtension**\]然後選取 \[**確定**\] 按鈕。  
  
9. 在資訊清單編輯器中，再選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
10. 在 \[**型別**\]方塊中，輸入 **SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  此項目會指定要加入 Visual Studio 擴充功能的自訂擴充功能。  如需詳細資訊，請參閱[資產的項目 \(VSX 結構描述\)](http://msdn.microsoft.com/zh-tw/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\] 清單項目。  
  
12. 在 \[**Project**\] 清單中，選取 \[**WebPartCommands**\]，然後選取 \[**確定**\] 按鈕。  
  
13. 在功能表列上，選擇， \[**組建**\]\[**建置方案**\]，然後確定方案編譯時未發生任何錯誤。  
  
14. 確定 WebPartNode 專案的建置輸出資料夾現已包含 WebPartNode.vsix 檔。  
  
     根據預設，建置輸出資料夾為 ..  \\bin\\Debug 資料夾，其位於專案檔案包含的資料夾下。  
  
## 測試擴充功能  
 您現在可以測試在 \[**伺服器總管**\] 的新 \[**Web 組件庫**\] 節點。  首先，在 Visual Studio 的實驗執行個體中開始偵錯擴充功能。  接著在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的實驗執行個體中使用新的 \[**Web 組件**\] 節點。  
  
#### 若要啟動對擴充功能的偵錯  
  
1.  重新啟動以管理認證的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，然後開啟 WebPartNode 方案。  
  
2.  在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔，然後將中斷點加入至 `NodeChildrenRequested` 和 `CreateWebPartNodes` 方法的第一行程式碼。  
  
3.  選擇 F5 鍵開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile% \\ AppData \\ Local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ Extensions \\ Contoso \\ Web 組件庫節點擴充伺服器總管的\\模糊並啟動 Visual Studio 的實驗執行個體。  您將會在 Visual Studio 的這個執行個體中測試專案項目。  
  
#### 若要測試擴充功能  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]實驗執行個體，在功能表列上，選擇 \[**檢視**\]， \[**伺服器總管**\]。  
  
2.  請執行下列步驟，如果您要用於測試的 SharePoint 網站不會出現在 \[**伺服器總管**\] 的 \[**SharePoint 連接**\] 節點下:  
  
    1.  在 \[**伺服器總管**\]，開啟 \[**SharePoint 連接**\] 的捷徑功能表，然後選取 \[**加入連結**\]。  
  
    2.  在 \[**加入 SharePoint 連接**\] 對話方塊中，輸入要連接的 SharePoint 網站的 URL，然後選擇 \[**確定**\] 按鈕。  
  
         若要指定 SharePoint 網站在您的開發電腦，輸入 **http:\/\/localhost**。  
  
3.  展開以顯示網站 URL 的網站連接節點 \(，然後展開子網站節點 \(例如， \[**合作網站**\]\)。  
  
4.  確認在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 另一個執行個體的程式碼在您之前於方法 `NodeChildrenRequested` ，然後選擇 F5 繼續偵錯專案的中斷點停止。  
  
5.  在 Visual Studio 的實驗執行個體中，確認名為 \[**Web 組件庫**\] 的新節點會出現在最上層網站節點，然後展開 \[**Web 組件庫**\] 節點。  
  
6.  確認在另一個 Visual Studio 執行個體中的程式碼在您之前於方法 `CreateWebPartNodes` ，然後選擇 F5 鍵繼續偵錯專案的中斷點停止。  
  
7.  在 Visual Studio 的實驗執行個體中，確認這個連接的站台的所有 Web 組件出現在 \[**伺服器總管**\] 的 \[**Web 組件庫**\] 節點下。  
  
8.  在 \[**伺服器總管**\]，開啟其中一個捷徑功能表 Web 組件，然後選取 \[**屬性**\]。  
  
9. 在您要偵錯 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 執行個體，請確認關於 Web 詳細資料的單獨出現在 \[**屬性**\] 視窗。  
  
## 從 Visual Studio 解除安裝擴充功能  
 完成測試擴充功能之後，解除安裝 Visual Studio 中的擴充功能。  
  
#### 若要解除安裝擴充功能  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]實驗執行個體，在功能表列上，選擇， \[**工具**\]\[**副檔名和更新**\]。  
  
     \[**副檔名和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選取 \[**Web 組件庫伺服器總管的節點擴充功能**\]，然後選取 \[**解除安裝**\] 按鈕。  
  
3.  在出現的對話方塊中，選取 \[**是**\] 按鈕確認您要解除安裝擴充功能，然後選取 \[**立即重新啟動**\] 按鈕完成解除安裝。  
  
4.  關閉 Visual Studio 的實驗執行個體和 WebPartNode 方案已開啟\) 的兩個執行個體執行 Visual Studio。  
  
## 請參閱  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  