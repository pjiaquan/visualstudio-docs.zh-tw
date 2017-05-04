---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  當您在 Visual Studio 中定義自訂類型的 SharePoint 專案項目，並為其建立與項目範本之間的關聯後，您也可以提供該範本專用的精靈。  您可以使用精靈，在使用者利用您的範本加入專案項目的新執行個體時，向使用者收集資訊。  您收集到的資訊可用來初始化專案項目。  
  
 在本逐步解說中，您將會在[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)示範的 \[自訂動作\] 專案項目中加入精靈。  當使用者將 \[自訂動作\] 專案項目加入至 SharePoint 專案時，精靈會收集此自訂動作的相關資訊 \(例如其位置和巡覽 URL，當使用者選取它\) 並將此資訊加入至新專案項目的 Elements.xml 檔案。  
  
 本逐步解說將示範下列工作：  
  
-   建立與項目範本有關聯之自訂 SharePoint 專案項目類型的精靈。  
  
-   SharePoint 定義類似於內建精靈的自訂精靈 UI 專案在 Visual Studio 的項目。  
  
-   使用可取代的參數，以您在精靈中收集到的資料初始化 SharePoint 專案檔。  
  
-   對精靈進行偵錯和測試。  
  
> [!NOTE]  
>  您可以下載包含已完成的專案、程式碼和其他檔案逐步解說的從下列位置的範例: [SharePoint 專案檔工具擴充性逐步解說](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## 必要條件  
 若要執行這個逐步解說，您必須先完成[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)，以建立 CustomActionProjectItem 方案。  
  
 此外，您的開發電腦上必須要有下列元件，才能完成此逐步解說：  
  
-   Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   Visual Studio 中的專案和項目範本專用的精靈。  如需詳細資訊，請參閱 [如何：搭配專案範本使用精靈](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)和 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。  
  
-   SharePoint 中的自訂動作。  如需詳細資訊，請參閱[自訂動作](http://go.microsoft.com/fwlink/?LinkId=177800) \(英文\)。  
  
## 建立精靈專案  
 若要完成這個逐步解說，您必須將專案加入至 CustomActionProjectItem 方案在 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)建立。  您將會在這個專案中實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面並定義精靈 UI。  
  
#### 若要建立精靈專案  
  
1.  在 Visual Studio 中，開啟 CustomActionProjectItem 方案  
  
2.  在 \[**方案總管**\]，開啟方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**視窗**\] 節點。  
  
4.  在 \[**新增專案**\] 對話方塊的頂端，確定 **.NET Framework 4.5** .NET Framework 版本的清單中選取。  
  
5.  選取 \[**WPF 使用者控制項程式庫**\] 專案範本，然後將專案命名為 **ItemTemplateWizard**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **ItemTemplateWizard** 專案加入至方案。  
  
6.  從專案刪除 UserControl1 項目。  
  
## 設定精靈專案  
 在建立精靈之前，您必須將 Windows Presentation Foundation \(WPF\) 視窗、程式碼檔案和組件參考加入至專案。  
  
#### 若要設定精靈專案  
  
1.  在 \[**方案總管**\]，開啟來自 \[**ItemTemplateWizard**\]專案節點的捷徑功能表，然後選取 \[**屬性**\]。  
  
2.  在 \[**專案設計工具**\]，請確認目標 Framework 設定為 .NET Framework 4.5。  
  
     對於 Visual C\# 專案中，您可以在 \[**應用程式**\] 選項的值。  對於 Visual Basic 專案中，您可以在 \[**編譯**\] 選項的值。  如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
3.  在 \[**ItemTemplateWizard**\]專案，請將 \[**視窗 \(WPF\)**\]項目加入至專案，然後 **WizardWindow**命名項目。  
  
4.  加入名為和的兩個字串 CustomActionWizard 程式碼檔案。  
  
5.  開啟 \[**ItemTemplateWizard**\]專案的捷徑功能表，然後選取 \[**新增參考**\]。  
  
6.  在 **參考管理員\- ItemTemplateWizard** 對話方塊，在 \[**組件**\] 節點底下，選取\[**延伸**\] 節點。  
  
7.  在下列組件旁邊的核取方塊，然後選取 \[**確定**\] 按鈕:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  在 \[**方案總管**\]，在 ItemTemplateWizard 專案的 \[**參考**\] 資料夾，選取 \[**EnvDTE**\]參考。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現 \[**參考**\] 資料夾。  
  
9. 在 \[**屬性**\] 視窗，變更 \[**內嵌 Interop 型別**\] 屬性的值變更為 \[**錯誤**\]。  
  
## 定義自訂動作的預設位置和 ID 字串  
 每個自訂動作都會有一個位置和 ID，分別由 Elements.xml 檔案中 `CustomAction` 項目的 `Location` 和 `GroupID` 屬性所指定。  在這個步驟中，您會為 ItemTemplateWizard 專案中的這些屬性定義一些有效字串。  當您完成本逐步解說時，這些字串寫入 Elements.xml 檔案在自訂動作專案項目，當使用者在精靈中指定位置和 ID。  
  
 為簡單起見，此範例僅支援可用預設位置和 ID 的子集。  如需完整清單，請參閱[預設的自訂動作位置和 ID](http://go.microsoft.com/fwlink/?LinkId=181964) \(英文\)。  
  
#### 若要定義預設位置和 ID 字串  
  
1.  開啟。  
  
2.  在 \[**ItemTemplateWizard**\]專案，請使用下列程式碼取代字串程式碼檔案中的程式碼。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## 建立精靈 UI  
 加入 XAML 以定義精靈的 UI，並加入一些程式碼以將精靈中的部分控制項繫結至 ID 字串。  您建立的精靈類似 SharePoint 專案內建精靈在 Visual Studio。  
  
#### 若要建立精靈 UI  
  
1.  在 \[**ItemTemplateWizard**\]專案，開啟 \[**WizardWindow.xaml**\]檔案的捷徑功能表，然後選取 \[**開啟**\] 以設計工具開啟的視窗。  
  
2.  在 \[XAML\] 檢視中，以下列 XAML 取代目前的 XAML。  這個 XAML 定義的 UI 包含標題、用於指定自訂動作行為的控制項和位於視窗底部的導覽按鈕。  
  
    > [!NOTE]  
    >  加入這個程式碼之後，將會出現一些編譯錯誤。  在後續步驟中加入程式碼時，這些錯誤將不存在。  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  在這個 XAML 會建立的視窗 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 從基底類別衍生。  當您將自訂 WPF 對話方塊加入至 Visual Studio 時，建議您從這個類別衍生自己的對話方塊具有一致的樣式與在 Visual Studio 的其他對話方塊並避免可能發生的強制回應對話方塊的問題。  如需詳細資訊，請參閱[建立和管理強制回應對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
3.  如果您正在開發 Visual Basic 專案，請從`Window` 項目的 `x:Class` 屬性的 `WizardWindow` 類別名稱移除 `ItemTemplateWizard` 命名空間。  這個項目在 XAML 的第一行。  當您完成時，第一行應類似下列程式碼:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  在 WizardWindow.xaml 檔案的程式碼後置檔案中，以下列程式碼取代目前的程式碼。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## 實作精靈  
 精靈的功能是藉由實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面來定義。  
  
#### 若要實作精靈  
  
1.  在 \[**ItemTemplateWizard**\]專案，開啟 \[**CustomActionWizard**\]程式碼檔，然後以下列程式碼取代此檔案中目前的程式碼:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## 檢查點  
 在逐步解說中進行至此處時，精靈的所有程式碼都會位於專案中。  建置專案，以確定在編譯時未發生任何錯誤。  
  
#### 若要建置您的專案  
  
1.  在功能表列上，選擇， \[**組建**\]\[**建置方案**\]。  
  
## 建立精靈與項目範本的關聯  
 現在您已實作精靈，接著必須與 \[**自訂動作**\] 項目範本藉由完成三個主要步驟:  
  
1.  使用強式名稱簽署精靈組件。  
  
2.  取得精靈組件的公開金鑰語彙基元。  
  
3.  將精靈組件的參考加入至 \[**自訂動作**\] 項目範本的 .vstemplate 檔案中。  
  
#### 若要使用強式名稱簽署精靈組件  
  
1.  在 \[**方案總管**\]，開啟來自 \[**ItemTemplateWizard**\]專案節點的捷徑功能表，然後選取 \[**屬性**\]。  
  
2.  選取 \[**簽署**\] 索引標籤上的 \[**簽署組件**\] 核取方塊。  
  
3.  在 \[**選擇強式名稱金鑰檔**\] 清單中， \[**\<New...\>**\] 選擇。  
  
4.  在 \[**建立強式名稱金鑰**\] 對話方塊中，輸入名稱，清除 \[**保護我的與密碼的金鑰檔**\] 核取方塊，然後選取 \[**確定**\] 按鈕。  
  
5.  在功能表列上，選擇， \[**組建**\]\[**建置方案**\]。  
  
#### 若要取得精靈組件的公開金鑰語彙基元  
  
1.  在 Visual Studio 命令提示字元視窗中，執行下列命令，以取代 *PathToWizardAssembly* 與完整路徑 ItemTemplateWizard 專案的 ItemTemplateWizard.dll 組件位於您開發電腦。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ItemTemplateWizard.dll 組件的公開金鑰語彙基元會寫入至 \[Visual Studio 命令提示字元\] 視窗。  
  
2.  讓 \[Visual Studio 命令提示字元\] 視窗保持開啟。  您將需要公開金鑰語彙基元完成下面的程序。  
  
#### 若要在 .vstemplate 檔案中加入精靈組件的參考  
  
1.  在 \[**方案總管**\]，展開 \[**ItemTemplate**\]專案節點，然後開啟 ItemTemplate.vstemplate 檔案。  
  
2.  在檔案結尾附近，於 `</TemplateContent>` 與 `</VSTemplate>` 標記之間加入 `WizardExtension` 項目。  用您在上一個程序取得的公開金鑰語彙基元取代 `PublicKeyToken` 屬性的 *YourToken* 值。  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     如需 `WizardExtension` 項目的詳細資訊，請參閱 [WizardExtension 項目 &#40;Visual Studio 範本&#41;](../extensibility/wizardextension-element-visual-studio-templates.md)。  
  
3.  儲存並關閉檔案。  
  
## 將可取代的參數加入至項目範本中的 Elements.xml 檔案  
 將數個可取代的參數加入至 ItemTemplate 專案中的 Elements.xml 檔案。  這些參數會以您先前定義之 `CustomActionWizard` 類別中的 `PopulateReplacementDictionary` 方法初始化。  當使用者將 \[自訂動作\] 專案項目加入至專案時，Visual Studio 即會自動在新的專案項目中，將 Elements.xml 檔案中的這些參數取代為使用者在精靈中所指定的值。  
  
 可取代的參數是以貨幣符號的語彙基元 \($\) 字元開頭和結尾。  除了定義您可取代的參數以外，您可以使用內建參數 SharePoint 專案系統定義和初始化。  如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
#### 若要將可取代的參數加入至 Elements.xml 檔案  
  
1.  在 ItemTemplate 專案中，以下列 XML 取代 Elements.xml 檔案的內容。  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     新的 XML 會將 `Id`、`GroupId`、`Location`、`Description` 和 `Url` 屬性的值變更為可取代的參數。  
  
2.  儲存並關閉檔案。  
  
## 將精靈加入至 VSIX 套件  
 在 VSIX 專案中的 source.extension.vsixmanifest 檔案中，加入精靈專案的參考，以便部署與包含專案項目的 VSIX 套件。  
  
#### 若要將精靈加入至 VSIX 套件  
  
1.  在 \[**方案總管**\]，開啟捷徑功能表在 CustomActionProjectItem 專案的 \[**source.extension.vsixmanifest**\]檔案，然後選取 \[**開啟**\] 開啟在資訊清單編輯器中開啟檔案。  
  
2.  在資訊清單編輯器中，選取 \[**資產**\] 索引標籤，然後選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
3.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.Assembly**\]。  
  
4.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
5.  在 \[**Project**\] 清單中，選取 \[**ItemTemplateWizard**\]，然後選取 \[**確定**\] 按鈕。  
  
6.  在功能表列上，選擇， \[**組建**\]\[**建置方案**\]，然後確定方案編譯時未發生任何錯誤。  
  
## 測試精靈  
 您現在可以測試精靈。  首先，偵錯在 Visual Studio 的實驗執行個體中 CustomActionProjectItem 方案的開始。  然後使用中 SharePoint 專案的自訂動作\] 專案項目中測試精靈在 Visual Studio 的實驗執行個體。  最後，建置並執行 SharePoint 專案，確認自訂動作功能正常。  
  
#### 開始偵錯方案  
  
1.  重新啟動以管理認證的 Visual Studio，然後開啟 CustomActionProjectItem 方案。  
  
2.  在 ItemTemplateWizard 專案中，開啟 CustomActionWizard 程式碼檔案，然後將中斷點加入至 `RunStarted` 方法的第一行程式碼。  
  
3.  在功能表列上，選擇 \[**偵錯**\]， \[**例外狀況**\]。  
  
4.  在 \[**例外狀況**\] 對話方塊中，確定已清除 **Common Language Runtime 例外狀況。** 的 \[**擲回**\] 和 \[**使用者未處理**\] 核取方塊，然後選取 \[**確定**\] 按鈕。  
  
5.  您可以選擇 F5 鍵開始偵錯，或者在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile% \\ AppData \\ Local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ Extensions \\ Contoso \\ Custom Action 專案項目\\模糊並啟動 Visual Studio 的實驗執行個體。  您在這個執行個體中測試專案項目 Visual Studio。  
  
#### 若要在 Visual Studio 中測試精靈  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
2.  展開 \[**Visual C\#**\] 或\[**Visual Basic**\] 節點 \(視語言而定的項目範本支援\)， \[**SharePoint**\] 展開節點，然後選取 \[**2010**\] 節點。  
  
3.  在專案範本清單中，選取 \[**SharePoint 2010 專案**\]，將專案命名為 **CustomActionWizardTest**，然後選取 \[**確定**\] 按鈕。  
  
4.  在 \[**SharePoint 自訂精靈**\]，輸入要用於偵錯的網站 URL，然後選擇 \[**完成**\] 按鈕。  
  
5.  在 \[**方案總管**\]，請開啟專案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新項目**\]。  
  
6.  在 **將新的項目\- CustomItemWizardTest** 對話方塊中，展開 \[**SharePoint**\] 節點，然後展開 \[**2010**\] 節點。  
  
7.  在專案項目清單中，選取 \[**自訂動作**\] 項目，然後選取 \[**新增**\] 按鈕。  
  
8.  確認另一個 Visual Studio 執行個體中的程式碼在您之前於 `RunStarted` 方法中設定的中斷點停止。  
  
9. 繼續選擇 F5 鍵偵錯專案，或在功能表列上，選擇\[**偵錯**\]， \[**繼續**\]。  
  
     \[SharePoint 自訂精靈\] 隨即出現。  
  
10. 在 \[**位置**\] 下，選取 \[**清單中編輯**\] 選項按鈕。  
  
11. 在 \[**群組 ID**\]清單中，選取 \[**通訊**\]。  
  
12. 在 \[**標題**\]方塊中，輸入 **SharePoint 開發人員中心**。  
  
13. 在 \[**Description**\]方塊中，輸入 **開啟 SharePoint 開發人員中心網站**。  
  
14. 在 \[**URL**\]方塊中，輸入 **http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**，然後選取 \[**完成**\] 按鈕。  
  
     isual Studio 加入名為的專案的 \[**CustomAction1**\]的項目並在編輯器中開啟 Elements.xml 檔案。  確認 Elements.xml 包含您在精靈中指定的值。  
  
#### 若要測試 SharePoint 中的自訂動作  
  
1.  在 Visual Studio 的實驗執行個體中，選擇 F5 鍵，或在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
     專案的 \[**網站 URL**\] 屬性在 SharePoint 網站封裝並部署至指定的這個自訂動作，因此，這個瀏覽器開啟此網站的預設網頁。  
  
    > [!NOTE]  
    >  如果 \[**已停用指令碼偵錯**\] 對話方塊出現時，請選擇 \[**是**\] 按鈕。  
  
2.  在 SharePoint 網站上的區域中，選取 \[**工作**\] 連結。  
  
     \[**工作–所有工作**\] 頁面隨即出現。  
  
3.  在功能區上的 \[**清單工具**\] 索引標籤上，選取 \[**清單**\] 索引標籤，然後，在 \[**設定**\] 群組中，選取 \[**清單設定**\]。  
  
     \[**列出設定**\] 頁面隨即出現。  
  
4.  在標題在網頁頂端附近 \[**通訊**\] 下，選取 \[**SharePoint 開發人員中心**\] 連結，確認瀏覽器開啟此網站 http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx，然後關閉瀏覽器。  
  
## 清理開發電腦  
 在您完成測試專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案項目範本。  
  
#### 若要清理開發電腦  
  
1.  在 Visual Studio 的實驗執行個體，在功能表列上，選擇， \[**工具**\]\[**副檔名和更新**\]。  
  
     \[**副檔名和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選取 \[**自訂動作專案項目**\] 副檔名，然後選取 \[**解除安裝**\] 按鈕。  
  
3.  在出現的對話方塊中，選取 \[**是**\] 按鈕確認您要解除安裝擴充功能，然後選取 \[**立即重新啟動**\] 按鈕完成解除安裝。  
  
4.  關閉 Visual Studio 的實驗執行個體和 CustomActionProjectItem 方案已開啟\) 的兩個執行個體執行 Visual Studio。  
  
## 請參閱  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：搭配專案範本使用精靈](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)   
 [根據中的自訂位置和 ID](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  