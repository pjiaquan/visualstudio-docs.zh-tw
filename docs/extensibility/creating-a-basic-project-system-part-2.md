---
title: "建立基本專案系統，第 2 部分 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "撰寫專案系統"
  - "專案系統"
  - "教學課程"
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 建立基本專案系統，第 2 部分
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本系列的第一個逐步解說 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md), ，示範如何建立基本專案系統。 此逐步解說建立基本專案系統上加入 Visual Studio 範本、 屬性頁和其他功能。 您必須先完成第一個逐步解說，才能啟動這一個。  
  
 這個逐步解說示範如何建立具有專案檔案名稱副檔名.myproj 的專案類型。 若要完成本逐步解說，您不需要建立自己的語言，因為本逐步解說借用現有的 Visual C\# 專案系統。  
  
 這個逐步解說示範如何完成這些工作:  
  
-   建立 Visual Studio 範本。  
  
-   部署 Visual Studio 範本。  
  
-   建立專案類型的子節點中 **新的專案** 對話方塊。  
  
-   可讓 Visual Studio 範本中的參數替代。  
  
-   建立專案屬性頁。  
  
> [!NOTE]
>  在本逐步解說的步驟是以 C\# 專案為基礎。 不過，除了副檔名的檔案和程式碼等特性，您可以使用相同的步驟是 Visual Basic 專案。  
  
## 建立 Visual Studio 範本  
 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md) 示範如何建立基本專案範本，並將它加入至專案系統。 它也示範如何使用此範本註冊使用 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 屬性，在系統登錄中寫入 \\Templates\\Projects\\SimpleProject\\ 資料夾的完整路徑。  
  
 藉由使用 Visual Studio 範本 \(.vstemplate 檔案\)，而不基本的專案範本，您可以控制的範本顯示於 **新的專案** 對話方塊，並以範本參數來取代。  .Vstemplate 檔案是描述如何將原始程式檔使用專案系統範本建立專案時要包含的 XML 檔案。 專案系統本身所收集的.vstemplate 檔和原始程式檔在.zip 檔案中，建置並部署的.zip 檔複製至位置，也是以 Visual Studio。 本逐步解說稍後詳細說明此程序。  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，開啟您依照建立 SimpleProject 方案 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)。  
  
2.  在 SimpleProjectPackage.cs 檔案中，尋找 ProvideProjectFactory 屬性。 取代第二個參數 \(專案名稱\) null，且具有".\\\\NullPath"，第四個參數 \(專案範本資料夾的路徑\)，如下所示。  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  加入名為 SimpleProject.vstemplate \\Templates\\Projects\\SimpleProject\\ 資料夾的 XML 檔案。  
  
4.  SimpleProject.vstemplate 的內容取代為下列程式碼。  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  在 **屬性** 視窗中，選取所有五個檔案的 \\Templates\\Projects\\SimpleProject\\ 資料夾，以及組 **建置動作** 至 **ZipProject**。  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \< TemplateData \> 區段決定的位置和外觀 SimpleProject 專案類型中的 **新的專案** 對話方塊，如下所示:  
  
-   \< 名稱 \> 項目名稱是 SimpleProject 應用程式的專案範本。  
  
-   \< 描述 \> 項目包含描述出現在 **新的專案** \] 對話方塊中選取專案範本時。  
  
-   \< i \> 項目會指定與 SimpleProject 專案類型一起出現的圖示。  
  
-   \< ProjectType \> 項目名稱中的專案類型 **新的專案** 對話方塊。 此名稱來取代 ProvideProjectFactory 屬性的專案名稱參數。  
  
    > [!NOTE]
    >  \< ProjectType \> 項目必須符合 `LanguageVsTemplate` 引數的 `ProvideProjectFactory` SimpleProjectPackage.cs 檔案中的屬性。  
  
 \< TemplateContent \> 一節說明在建立新的專案時，會產生這些檔案:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 這三個檔案有 `ReplaceParameters` 設為 true，可讓參數替代。  Program.cs 檔案具有 `OpenInEditor` 設為 true，這樣會造成要建立專案時，程式碼編輯器中開啟的檔案。  
  
 如需 Visual Studio 範本結構描述中元素的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
> [!NOTE]
>  如果專案具有一個以上的 Visual Studio 範本，每一個範本是另一個資料夾中。 在該資料夾中的每個檔案必須具有 **建置動作** 設 **ZipProject**。  
  
## 加入最小.vsct 檔案  
 Visual Studio 必須能夠辨識新的或修改 Visual Studio 範本安裝模式中執行。 安裝模式需要.vsct 檔必須存在。 因此，您必須將最小.vsct 檔加入專案。  
  
1.  加入名為 SimpleProject.vsct SimpleProject 專案的 XML 檔案。  
  
2.  SimpleProject.vsct 檔案的內容取代為下列程式碼。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  設定 **建置動作** 到這個檔案的 **VSCTCompile**。 您可以只在.csproj 檔案中，不會在 **屬性** 視窗。 請確定 **建置動作** 這個檔案設定為 **無** 此時。  
  
    1.  SimpleProject 節點上按一下滑鼠右鍵，然後按一下 \[ **編輯 SimpleProject.csproj**。  
  
    2.  在.csproj 檔案中，找出 SimpleProject.vsct 項目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  變更的建置動作 **VSCTCompile**。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  專案檔，然後關閉編輯器。  
  
    5.  儲存 \[SimpleProject\] 節點，然後在 **方案總管\] 中** 按一下 **重新載入專案**。  
  
## 檢查 Visual Studio 範本建立步驟  
 當.vstemplate 檔已變更，或重建專案，其中包含.vstemplate 檔案 VSPackage 專案建置系統通常以安裝模式執行 Visual Studio。 您可以遵循藉由設定為 Normal 或更高版本的 MSBuild 的詳細資訊層級。  
  
1.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。  
  
2.  展開 **專案和方案** 節點，然後再選取 **建置並執行**。  
  
3.  設定 **MSBuild 專案建置輸出詳細程度** 至 **正常**。 按一下 \[**確定**\]。  
  
4.  重建 SimpleProject 專案。  
  
 建置步驟，建立.zip 專案檔應該類似下列的範例。  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## 部署 Visual Studio 範本  
 Visual Studio 範本不包含路徑資訊。 因此，範本.zip 檔案必須部署至位置，也是以 Visual Studio。 ProjectTemplates 資料夾的位置通常是 **\< %LOCALAPPDATA%\> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**。  
  
 若要部署您專案的 factory，安裝程式必須具有系統管理員權限。 它會部署在 Visual Studio 的 \[安裝\] 節點下的範本: **...\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates**。  
  
## 測試 \[Visual Studio 範本  
 測試您的專案 factory，以查看是否會使用 Visual Studio 範本建立專案階層架構。  
  
1.  重設 Visual Studio SDK experimental 執行個體。  
  
     在 [!INCLUDE[win7](../debugger/includes/win7_md.md)]: 在 \[開始\] 功能表中，找到 **Microsoft Visual Studio\/Microsoft Visual Studio SDK\/工具** 資料夾，然後再選取 **重設 Microsoft Visual Studio Experimental 執行個體**。  
  
     更新版本的 Windows 上: 在 \[開始\] 畫面中，輸入 **重設 Microsoft Visual Studio \< 版本 \> 實驗執行個體**。  
  
2.  命令提示字元\] 視窗隨即出現。 當您看到幾個字 `Press any key to continue`, ，按 enter 鍵。 在視窗關閉之後，開啟 Visual Studio。  
  
3.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體隨即出現。  
  
4.  在實驗執行個體中，建立 SimpleProject 專案。 在 **新的專案** 對話方塊中，選取 **SimpleProject**。  
  
5.  您應該會看到 SimpleProject 的新執行個體。  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## 建立專案類型的子節點  
 您可以加入的專案型別節點中子節點 **新的專案** 對話方塊。  比方說，SimpleProject 專案類型，您有子節點的主控台應用程式、 視窗應用程式、 web 應用程式等等。  
  
 變更專案檔，並將 \< OutputSubPath \> 子系加入至 \< ZipProject \> 項目會建立子節點。 複製範本時，組建或部署期間，每個子節點會成為專案範本資料夾的子資料夾。  
  
 本節說明如何建立主控台 SimpleProject 專案類型的子節點。  
  
1.  重新命名 \\Templates\\Projects\\ConsoleApp\\ \\Templates\\Projects\\SimpleProject\\ 資料夾。  
  
2.  在 **屬性** \] 視窗中，選取 \\Templates\\Projects\\ConsoleApp\\ 資料夾中的所有五個檔案，並確定 **建置動作** 設為 **ZipProject**。  
  
3.  在 SimpleProject.vstemplate 檔案中，新增下列這一行結尾的 \< TemplateData \> 區段中，結尾標記前面。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     這會導致出現在主控台的子節點和 SimpleProject 父節點，也就是一層的子節點中的主控台應用程式範本。  
  
4.  儲存 SimpleProject.vstemplate 檔案。  
  
5.  在.csproj 檔案中，加入 \< OutputSubPath \> 每個 ZipProject 項目。 卸載的專案，並編輯專案檔。  
  
6.  找出 \< ZipProject \> 項目。 每個 \< ZipProject \> 項目，加入 \< OutputSubPath \> 項目，並指定其值為主控台。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  將這個 \< p \> 加入至專案檔:  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  儲存專案檔，並重新載入專案。  
  
## 測試專案類型的子節點  
 測試修改過的專案檔案，以查看是否 **主控台** 子節點會出現在 **新的專案** 對話方塊。  
  
1.  執行 **重設 Microsoft Visual Studio 實驗執行個體** 工具。  
  
2.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體應該會出現  
  
3.  在 **新的專案** \] 對話方塊中，按一下 \[ **SimpleProject** 節點。**主控台應用程式** 範本應該會出現在 **範本** 窗格。  
  
4.  展開 **SimpleProject** 節點。**主控台** 子節點應該會出現。**SimpleProject 應用程式** 範本仍會出現在 **範本** 窗格。  
  
5.  。 按一下 \[ **取消** ，停止偵錯  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## 專案範本參數  
 [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md) 示範如何覆寫 `ProjectNode.AddFileFromTemplate` 方法，以進行基本的一種範本參數替代。 本章節會教導如何使用更複雜的 Visual Studio 範本參數。  
  
 當您使用 Visual Studio 範本中的建立專案時 **新的專案** 對話方塊中，以自訂專案範本會以取代參數字串。 樣板參數是特殊的語彙基元開始和結束都錢幣符號，例如 $time$。 下列兩個參數會啟用自訂範本為基礎的專案中特別有用:  
  
-   $ $GUID \[1\-10\] 取代為新的 Guid。 您可以指定最多 10 個唯一的 Guid，例如，$guid1$。  
  
-   $safeprojectname$ 是中的使用者所提供的名稱 **新的專案** 對話方塊中，修改以移除所有 unsafe 字元和空格。  
  
 如需範本參數的完整清單，請參閱 [樣板參數](../ide/template-parameters.md)。  如果您想要建立您自己的自訂範本參數，請參閱 [NIB: How to: 將傳遞至範本的自訂參數](http://msdn.microsoft.com/zh-tw/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)。  
  
#### 將專案範本參數  
  
1.  在 SimpleProjectNode.cs 檔案中，移除 `AddFileFromTemplate` 方法。  
  
2.  在 \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj 檔案中，找出 \< RootNamespace \> 屬性，並將其值變更為 $safeprojectname$。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  在 \\Templates\\Projects\\SimpleProject\\Program.cs 檔案中，請以下列程式碼取代檔案的內容:  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  重建 SimpleProject 專案並開始偵錯。 實驗執行個體應該會出現。  
  
5.  建立新的 SimpleProject 主控台應用程式。 \(在 **專案類型** 窗格中，選取 **SimpleProject**。 在 **Visual Studio 安裝的範本**, ，請選取 **主控台應用程式**。\)  
  
6.  在新建立專案中，開啟 Program.cs。 看起來應該如下所示 \(在檔案中的 GUID 值將會不同\)。:  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## 建立專案屬性頁  
 讓使用者可以檢視並變更您的範本為基礎的專案中的屬性，您可以建立您的專案類型的屬性頁。 本節說明如何建立組態無關的屬性頁。 這個基本的屬性頁會使用屬性方格來顯示在屬性頁面類別中公開 \(expose\) 的公用屬性。  
  
 衍生您的屬性頁面類別，從 `SettingsPage` 基底類別。 所提供的 \[屬性\] 方格 `SettingsPage` 類別知道最基本資料型別，並知道如何顯示它們。  此外， `SettingsPage` 類別知道如何保存專案檔的屬性值。  
  
 您在這一節中建立屬性頁可讓您變更並儲存這些專案屬性:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace。  
  
1.  在 SimpleProjectPackage.cs 檔案中，加入下列 `ProvideObject` 屬性設定為 `SimpleProjectPackage` 類別:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     這會註冊屬性頁類別 `GeneralPropertyPage` com。  
  
2.  在 SimpleProjectNode.cs 檔案中，加入至這兩個覆寫的方法 `SimpleProjectNode` 類別:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     這兩種方法會傳回陣列的屬性頁的 Guid。  GeneralPropertyPage GUID 是唯一的項目，在陣列中，所以 **屬性頁** 對話方塊將會顯示一個頁面。  
  
3.  新增名為 GeneralPropertyPage.cs SimpleProject 專案的類別檔案。  
  
4.  使用下列程式碼來取代此檔案的內容:  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     `GeneralPropertyPage` 類別會公開三個公用屬性 AssemblyName、 OutputType 和 RootNamespace。 因為 AssemblyName 不具 set 方法，就會顯示為唯讀屬性。 OutputType 是列舉的常數，因此它會顯示為下拉式清單中。  
  
     `SettingsPage` 基底類別提供 `ProjectMgr` 保存屬性。`BindProperties` 方法會使用 `ProjectMgr` 擷取保存的屬性值，並設定對應的屬性。`ApplyChanges` 方法會使用 `ProjectMgr` 以取得屬性的值，並將其保存在專案檔。 這個屬性設定方法會設定 `IsDirty` 指出屬性需要保存為 true。  當您儲存專案或方案時，就會發生持續性。  
  
5.  重建 SimpleProject 方案並開始偵錯。 實驗執行個體應該會出現。  
  
6.  在實驗執行個體中，建立新的 SimpleProject 應用程式。  
  
7.  Visual Studio 會呼叫您使用 Visual Studio 範本建立專案的專案 factory。 程式碼編輯器中開啟新的 Program.cs 檔案。  
  
8.  以滑鼠右鍵按一下專案節點中的 **方案總管\] 中**, ，然後按一下 \[ **屬性**。**屬性頁** 對話方塊隨即出現。  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## 測試專案屬性頁  
 現在您可以測試是否可以修改，並變更屬性值。  
  
1.  在 **{1\>myconsoleapplication 屬性頁** 對話方塊中， **DefaultNamespace** 至 **MyApplication**。  
  
2.  選取 **OutputType** 屬性，然後再選取 **類別庫**。  
  
3.  按一下 \[ **套用**, ，然後按一下 \[ **確定**。  
  
4.  重新開啟 **屬性頁** 對話方塊並確認您的變更已保存下來。  
  
5.  關閉 Visual Studio 的實驗執行個體。  
  
6.  重新開啟的實驗執行個體。  
  
7.  重新開啟 **屬性頁** 對話方塊並確認您的變更已保存下來。  
  
8.  關閉 Visual Studio 的實驗執行個體。  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")