---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  當您部署 SharePoint 專案時， Visual Studio 會執行一系列的部署步驟按照特定順序。  Visual Studio 包含許多內建的部署步驟，但是您也可以建立自己的步驟。  
  
 在這個逐步解說中，您將建立自訂部署步驟升級在執行 SharePoint 的伺服器上的方案。  Visual Studio 包含許多工作，例如撤銷或加入方案的內建部署步驟，不過，它不包含升級方案部署步驟。  根據預設，在中，當您部署 SharePoint 方案時， Visual Studio 會先撤銷方案 \(如果已部署\) 然後重新部署整個方案。  如需內建部署步驟的詳細資訊，請參閱[部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立執行兩項主要工作的 Visual Studio 擴充功能：  
  
    -   副檔名會定義自訂部署步驟升級 SharePoint 方案。  
  
    -   副檔名建立定義新的部署組態，這是一組部署步驟針對指定的專案執行的專案擴充功能。  新的部署組態包括自訂部署步驟和數個內建的部署步驟。  
  
-   建立擴充組件呼叫的兩個自訂 SharePoint 命令。  SharePoint 命令是在伺服器物件模型可以由擴充組件呼叫使用 SharePoint API 為的方法。  如需詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   建置 Visual Studio Extension \(VSIX\) 套件以部署這兩個組件。  
  
-   測試新的部署步驟。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本逐步解說使用 SDK 中的 \[**VSIX 專案**\] 範本建立 VSIX 套件，以部署擴充功能。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   使用的 SharePoint 伺服器物件模型。  如需詳細資訊，請參閱[使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796) \(英文\)。  
  
-   SharePoint 方案。  如需詳細資訊，請參閱[方案概觀](http://go.microsoft.com/fwlink/?LinkId=169422) \(英文\)。  
  
-   升級 SharePoint 方案。  如需詳細資訊，請參閱[升級方案](http://go.microsoft.com/fwlink/?LinkId=177802) \(英文\)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立三個專案:  
  
-   VSIX 專案，用於建立 VSIX 套件以部署擴充功能。  
  
-   類別庫專案，可實作擴充功能。  這個專案必須以 .NET Framework 4.5。  
  
-   類別庫專案，可定義自訂 SharePoint 命令。  這個專案必須以才能執行。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**擴充性**\] 節點。  
  
    > [!NOTE]  
    >  為，當您安裝 Visual Studio SDK， \[**擴充性**\] 有節點的。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
4.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
5.  選取 \[**VSIX 專案**\] 範本，將專案命名為 **UpgradeDeploymentStep**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **UpgradeDeploymentStep** 專案加入至 \[**方案總管**\]。  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\]，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**視窗**\] 節點。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] 。  
  
4.  選取 \[**類別庫**\] 專案範本，命名 **DeploymentStepExtension**專案，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 隨即將 \[**DeploymentStepExtension**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
#### 若要建立 SharePoint 命令專案  
  
1.  在 \[**方案總管**\]，開啟 UpgradeDeploymentStep 方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\]，然後選取 \[**視窗**\] 節點。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 3.5**\] 。  
  
4.  選取 \[**類別庫**\] 專案範本，命名 **SharePointCommands**專案，然後選取 \[**確定**\] 按鈕。  
  
     Visual Studio 會將 **SharePointCommands** 專案加入至方案，並且開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定專案  
 在您撰寫程式碼建立自訂部署步驟之前，您必須將程式碼檔案和組件參考，因此，您必須設定專案。  
  
#### 若要設定 DeploymentStepExtension 專案  
  
1.  在 \[**DeploymentStepExtension**\]專案中，加入名稱如下的兩個程式碼檔:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  開啟在 DeploymentStepExtension 專案的捷徑功能表，然後選取 \[**新增參考**\]。  
  
3.  在 \[**Framework**\] 索引標籤，為 System.ComponentModel.Composition 組件選取核取方塊。  
  
4.  在 \[**延伸**\] 索引標籤，為 Microsoft.VisualStudio.SharePoint 組件選取核取方塊，然後選取 \[**確定**\] 按鈕。  
  
#### 若要設定 SharePointCommands 專案  
  
1.  在 \[**SharePointCommands**\]專案中，加入名為 Commands 的程式碼檔。  
  
2.  在 \[**方案總管**\]，在 \[**SharePointCommands**\]專案節點的捷徑功能表，然後選取 \[**新增參考**\]。  
  
3.  在 \[**延伸**\] 索引標籤，為下列組件選取核取方塊，然後按一下按鈕 \[**確定**\]  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## 定義自訂部署步驟  
 建立定義升級部署步驟的類別。  為定義部署步驟，類別會實作 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 介面。  在您要定義自訂部署步驟時實作此介面。  
  
#### 若要定義自訂部署步驟  
  
1.  在 \[**DeploymentStepExtension**\]專案，開啟 UpgradeStep 程式碼檔，然後將下列程式碼貼入其中。  
  
    > [!NOTE]  
    >  加入這個程式碼之後，專案會出現一些編譯錯誤，不過，它們會消失，當您將在稍後的步驟中的程式碼。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## 建立包含自訂部署步驟的部署組態  
 建立新的部署組態建立專案擴充功能，包括數個內建的部署步驟和新的升級部署步驟。  藉由建立這個擴充功能，您可以在 SharePoint 專案說明 SharePoint 開發人員使用升級部署步驟。  
  
 為建立部署組態，類別會實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。  在您要建立 SharePoint 專案擴充功能時實作此介面。  
  
#### 若要建立部署組態  
  
1.  在 \[**DeploymentStepExtension**\]專案，開啟 DeploymentConfigurationExtension 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## 建立自訂 SharePoint 命令  
 建立的呼叫 SharePoint 伺服器物件模型的兩個自訂命令。  其中一個命令會判斷是否已部署方案；另一個命令則會升級方案。  
  
#### 若要定義 SharePoint 命令  
  
1.  在 \[**SharePointCommands**\]專案，開啟 Commands 程式碼檔案，然後將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## 檢查點  
 在逐步解說中進行至此處時，自訂部署步驟的所有程式碼和 SharePoint 命令都會位於專案中。  建置它們，以確保編譯時未發生任何錯誤。  
  
#### 建立專案  
  
1.  在 \[**方案總管**\]，開啟 \[**DeploymentStepExtension**\]專案的捷徑功能表，然後選取 \[**組建**\]。  
  
2.  開啟 \[**SharePointCommands**\]專案的捷徑功能表，然後選取 \[**組建**\]。  
  
## 建立 VSIX 套件以部署擴充功能  
 若要部署擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案中的 source.extension.vsixmanifest 檔案來設定 VSIX 套件。  然後您可以建置方案建立 VSIX 套件。  
  
#### 若要設定和建立 VSIX 套件  
  
1.  在 \[**方案總管**\]，在 \[**UpgradeDeploymentStep**\]專案中，開啟 \[**source.extension.vsixmanifest**\]檔案的捷徑功能表，然後選取 \[**開啟**\]。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。  source.extension.vsixmanifest 檔案是所有 VSIX 套件所需要的 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**產品名稱**\]方塊中，輸入 **升級 SharePoint 專案的部署步驟。**。  
  
3.  在 \[**作者**\]方塊中，輸入 **Contoso**。  
  
4.  在 \[**Description**\]方塊中，輸入 **提供可用於 SharePoint 專案的自訂升級部署步驟**。  
  
5.  在編輯器中 \[**資產**\] 索引標籤上，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
6.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
8.  在 \[**Project**\] 清單中，選取 \[**DeploymentStepExtension**\]，然後選取 \[**確定**\] 按鈕。  
  
9. 在資訊清單編輯器中，再選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
10. 在 \[**型別**\]清單中，輸入 **SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  此項目會指定要加入 Visual Studio 擴充功能的自訂擴充功能。  如需詳細資訊，請參閱[資產的項目 \(VSX 結構描述\)](http://msdn.microsoft.com/zh-tw/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
12. 在 \[**Project**\] 清單中，選取 \[**SharePointCommands**\]，然後選取 \[**確定**\] 按鈕。  
  
13. 在功能表列上，選擇， \[**組建**\]\[**建置方案**\]，然後確定方案編譯時未發生任何錯誤。  
  
14. 確定 UpgradeDeploymentStep 專案的建置輸出資料夾現已包含 UpgradeDeploymentStep.vsix 檔。  
  
     根據預設，建置輸出資料夾為 ..  \\bin\\Debug 資料夾，其位於專案檔案包含的資料夾下。  
  
## 準備測試升級部署步驟  
 若要測試升級部署步驟，您必須先將範例方案部署到 SharePoint 網站。  首先，在 Visual Studio 的實驗執行個體中偵錯擴充功能。  然後建立清單定義和清單執行個體使用測試部署步驟，然後部署到 SharePoint 網站。  接著，請修改清單定義和清單執行個體並重新部署這些項目預設部署程序會示範如何覆寫 SharePoint 網站的方案。  
  
 稍後在本逐步解說中，您將修改清單定義和清單執行個體，您可以在 SharePoint 網站並將它們升級。  
  
#### 若要啟動對擴充功能的偵錯  
  
1.  重新啟動以管理認證的 Visual Studio，然後開啟 UpgradeDeploymentStep 方案。  
  
2.  在 DeploymentStepExtension 專案，開啟 UpgradeStep 程式碼檔，然後將中斷點加入至 `CanExecute` 和 `Execute` 方法的第一行程式碼。  
  
3.  您可以選擇 F5 鍵開始偵錯，或在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
4.  Visual Studio 會將擴充功能安裝至 %UserProfile% \\ AppData \\ Local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ Extensions \\ Contoso \\升級部署步驟 SharePoint 專案的\\模糊並啟動 Visual Studio 的實驗執行個體。  您在這個執行個體中測試升級部署步驟 Visual Studio。  
  
#### 若要建立 SharePoint 專案與清單定義和清單執行個體  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\]節點，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
3.  \[\] 對話方塊的頂端，確定 \[**.NET Framework 3.5**\] 出現的 .NET Framework 版本的清單。  
  
     [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 的專案需要此版本的 .NET Framework。  
  
4.  在專案範本清單中，選取 \[**SharePoint 2010 專案**\]，將專案命名為 \[**EmployeesListDefinition**\]，然後選取 \[**確定**\] 按鈕。  
  
5.  在 \[**SharePoint 自訂精靈**\]，輸入要用於偵錯的網站 URL。  
  
6.  在 \[**此 SharePoint 方案的信任層級為何**\] 下，選取 \[**部署為陣列方案**\] 選項按鈕。  
  
    > [!NOTE]  
    >  升級部署步驟不支援沙箱化方案。  
  
7.  選取 \[**完成**\] 按鈕。  
  
     建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition 專案。  
  
8.  開啟 EmployeesListDefinition 專案的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新項目**\]。  
  
9. 在 \[**將新的項目– EmployeesListDefinition**\] 對話方塊中，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
10. 選取 \[**清單**\] 項目範本，命名項目 **員工清單**，然後選取 \[**新增**\] 按鈕。  
  
     \[SharePoint 自訂精靈的外觀  
  
11. 在 \[**選擇清單設定**\] 頁面中，確認下列設定，然後選取 \[**完成**\] 按鈕:  
  
    1.  **員工清單** 出現 \[**您想要為清單中顯示名稱?**\]方塊。  
  
    2.  \[**建立以一個自訂的清單:**\]選項按鈕已選取。  
  
    3.  \[**預設 \(空白\)**\] 在 \[**建立以一個自訂的清單:**\]清單中選取。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立標題資料行和單一空白執行個體的員工清單項目並開啟清單設計工具。  
  
12. 在清單中，設計工具 \[**資料行**\] 索引標籤上，選取 \[**輸入新的或現有的資料行名稱**\] 行，然後將 \[**資料行顯示名稱**\] 清單中的下列資料行:  
  
    1.  名稱  
  
    2.  公司  
  
    3.  企業呼叫  
  
    4.  電子郵件  
  
13. 儲存所有檔案，然後關閉清單設計工具。  
  
14. 在 \[**方案總管**\]，展開 \[**員工清單**\] 節點，然後展開 \[**員工清單執行個體**\] 子節點。  
  
15. 在 Elements.xml 檔案中，以下列 XML 取代此檔案中的預設 XML。  這個 XML 變更清單的名稱到 \[**員工**\] 並加入名為 Jim Hance 的員工名稱的資訊。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. 儲存並關閉 Elements.xml 檔案。  
  
17. 開啟 EmployeesListDefinition 專案的捷徑功能表，然後選取 \[**開啟**\] 或 \[**屬性**\]。  
  
     屬性設計工具中開啟。  
  
18. 在 \[**SharePoint**\] 選項，明確 \[**偵錯後自動撤銷**\] 核取方塊，然後儲存屬性。  
  
#### 若要部署清單定義和清單執行個體  
  
1.  在 \[**方案總管**\]，選取 \[**EmployeesListDefinition**\]專案節點。  
  
2.  在 \[**屬性**\] 視窗中，確定 \[**現用部署組態**\] 屬性已設定為 \[**預設**\]。  
  
3.  選擇 F5 鍵，或在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
4.  驗證專案建置成功，這個瀏覽器開啟至 SharePoint 網站， \[快速啟動\] 列的 \[**清單**\] 項目包括新 \[**員工**\] 清單，因此， \[**員工**\] 清單包含 Jim Hance 輸入。  
  
5.  結束這個瀏覽器。  
  
#### 若要修改清單定義和清單執行個體並且重新部署  
  
1.  在 EmployeesListDefinition 專案，開啟為 \[**員工清單執行個體**\] 專案項目之子系的 Elements.xml 檔案。  
  
2.  移除 `Data` 項目及其子項目，以便從清單移除 Jim Hance 這個項目。  
  
     當您完成時，檔案應包含下列 XML。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  儲存並關閉 Elements.xml 檔案。  
  
4.  開啟 \[**員工清單**\] 專案項目的捷徑功能表，然後選取 \[**開啟**\] 或 \[**屬性**\]。  
  
5.  在清單設計工具中，選取 \[**檢視**\] 索引標籤。  
  
6.  在 \[**選取的欄**\] 清單中，選取 \[**附件**\]，然後選取\<移動的索引鍵資料行移至 \[**可用的資料行**\] 清單。  
  
7.  重複以上步驟從 \[**選取的欄**\] 清單中移動 \[**企業呼叫**\] 資料行移至 \[**可用的資料行**\] 清單。  
  
     這個動作會移除 SharePoint 網站上，\[**員工**\] 清單的預設檢視中的這些欄位。  
  
8.  您可以選擇 F5 鍵開始偵錯，或在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
9. 確認 \[**部署衝突**\] 對話方塊出現。  
  
     這個對話方塊會顯示 Visual Studio 嘗試部署方案 \(清單執行個體\) 加入至該方案已部署的 SharePoint 網站。  這個對話方塊不會出現在之後執行升級部署步驟在這個逐步解說。  
  
10. 在 \[**部署衝突**\] 對話方塊中，選取 \[**自動解決**\] 選項按鈕。  
  
     Visual Studio 會刪除 SharePoint 網站的清單執行個體，部署專案中的清單項目，然後開啟 SharePoint 網站。  
  
11. 在快速啟動列上的 \[**清單**\] 部分，選取 \[**員工**\] 清單，然後確認下列詳細資料:  
  
    -   \[**附件**\] 和 \[**家用電話**\] 資料行不會出現在清單的此檢視。  
  
    -   這個清單是空的。  若您使用 \[**預設**\] 部署組態重新部署方案，\[**員工**\] 清單就會被專案中新的空清單取代。  
  
## 測試部署步驟  
 您現在可以開始測試升級部署步驟。  首先將項目加入至 SharePoint 中的清單執行個體。  接著將清單定義和清單執行個體，將它們升級至 SharePoint 網站，並確認升級部署步驟不覆寫新項目。  
  
#### 若要手動將項目加入至清單  
  
1.  在 SharePoint 網站的功能區，在 \[**列出工具**\] 索引標籤中，選取 \[**項目**\] 索引標籤。  
  
2.  在 \[**新增**\] 群組中，選取 \[**新項目**\]。  
  
     或者，您可以選取項目清單的 \[**將新的項目。**\] 連結。  
  
3.  在 \[**員工–新項目**\] 視窗 \[**標題**\] ，在方塊中，輸入 **安裝管理員**。  
  
4.  在 \[**名稱**\]方塊中，輸入 **安迪**。  
  
5.  在 \[**公司**\]方塊中，輸入 **Contoso**。  
  
6.  選取 \[**儲存**\] 按鈕，確認新項目出現在清單中，然後關閉這個瀏覽器。  
  
     稍後在本逐步解說中，您將使用此項目確認升級部署步驟不會覆寫此清單的內容。  
  
#### 若要測試升級部署步驟  
  
1.  在 Visual Studio 的實驗執行個體，在 \[**方案總管**\]，開啟 \[**EmployeesListDefinition**\]專案節點的捷徑功能表，然後選取 \[**屬性**\]。  
  
     屬性在編輯器\/設計工具中開啟。  
  
2.  在 \[**SharePoint**\] 索引標籤，將 \[**現用部署組態**\] 屬性對 \[**升級**\]。  
  
     這個自訂部署組態包括新的升級部署步驟。  
  
3.  開啟 \[**員工清單**\] 專案項目的捷徑功能表，然後選取 \[**屬性**\] 或 \[**開啟**\]。  
  
     屬性在編輯器\/設計工具中開啟。  
  
4.  在 \[**檢視**\] 索引標籤上，選取 \[**電子郵件**\] 資料行，然後選取 \[**\<**\]索引鍵從 \[**選取的欄**\] 捲動清單控制項移至 \[**可用的資料行**\] 清單。  
  
     這個動作會移除 SharePoint 網站上，\[**員工**\] 清單的預設檢視中的這些欄位。  
  
5.  您可以選擇 F5 鍵開始偵錯，或在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
6.  確認另一個 Visual Studio 執行個體中的程式碼在您之前於 `CanExecute` 方法中設定的中斷點停止。  
  
7.  再次選擇 F5 鍵，或在功能表列上，選擇\[**偵錯**\]， \[**繼續**\]。  
  
8.  確認程式碼在您之前於 `Execute` 方法中設定的中斷點停止。  
  
9. 選擇 F5 鍵，或在功能表列上，選擇\[**偵錯**\]， \[**繼續**\] 最後的時間。  
  
     這個瀏覽器中開啟 SharePoint 網站。  
  
10. 在快速啟動區中 \[**清單**\] 部分，選取 \[**員工**\] 清單，然後確認下列詳細資料:  
  
    -   您之前手動加入的項目 \(安迪，安裝管理員\) 仍然在清單中。  
  
    -   \[**企業呼叫**\] 和 \[**電子郵件地址**\] 資料行不會出現在清單的此檢視。  
  
     \[**升級**\] 部署組態會修改 SharePoint 網站上現有的 \[**員工**\] 清單執行個體。  如果您使用 \[**預設**\] 部署組態，而不是 \[**升級**\] 組態，則可能發生部署衝突。  Visual Studio 會透過取代 \[**員工**\] 清單解決衝突，因此，安迪項目，安裝管理員，將刪除。  
  
## 清理開發電腦  
 在您完成測試升級部署步驟之後，從 SharePoint 網站移除清單執行個體和清單定義，並且從 Visual Studio 移除部署步驟擴充。  
  
#### 若要從 SharePoint 網站移除清單執行個體  
  
1.  如果清單尚未開啟，開啟 SharePoint 網站的 \[**員工**\] 清單。  
  
2.  在 SharePoint 網站的功能區，請選取 \[**列出工具**\] 索引標籤，然後選取 \[**清單**\] 索引標籤。  
  
3.  在 \[**設定**\] 群組中，選取 \[**清單設定**\] 項目。  
  
4.  在 \[**使用權限和管理**\] 下，選取 \[**刪除這個清單**\] 命令，選取 \[**確定**\] 確認您要傳送至資源回收筒\] 清單，然後關閉這個瀏覽器。  
  
#### 若要從 SharePoint 網站移除清單定義  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇 \[**組建**\]， \[**撤銷**\]。  
  
     Visual Studio 會撤銷 SharePoint 網站上的清單定義。  
  
#### 若要解除安裝擴充功能  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇， \[**工具**\]\[**副檔名和更新**\]。  
  
     \[**副檔名和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選取 \[**升級 SharePoint 專案的部署步驟。**\]，然後選取 \[**解除安裝**\] 命令。  
  
3.  在出現的對話方塊中，選取 \[**是**\] 確認您要解除安裝擴充功能，然後選取 \[**立即重新啟動**\] 完成解除安裝。  
  
4.  關閉 Visual Studio 的實驗執行個體和 UpgradeDeploymentStep 方案已開啟\) 的兩個執行個體執行 Visual Studio。  
  
## 請參閱  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  