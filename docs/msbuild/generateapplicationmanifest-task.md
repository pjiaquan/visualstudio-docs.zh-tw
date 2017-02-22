---
title: "GenerateApplicationManifest Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateApplicationManifest task"
  - "HostInBrowser property (MSBuild)"
  - "GenerateApplicationManifest task [MSBuild]"
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateApplicationManifest Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單或原生 \(Native\) 資訊清單。  原生資訊清單在描述元件時，會定義元件的唯一識別 \(Identity\)，並識別組成元件的所有組件 \(Assembly\) 和檔案。  在指出應用程式的進入點並指定應用程式的安全性層級之後，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式清單就可以擴充原生資訊清單。  
  
## 參數  
 下表說明 `GenerateApplicationManifest` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AssemblyName`|選擇性 `String` 參數。<br /><br /> 為已產生的資訊清單指定組件識別的 `Name` 欄位。  如果沒有指定此參數，就會從 `EntryPoint` 或 `InputManifest` 參數推斷名稱。  如果無法建立名稱，工作便會擲出錯誤。|  
|`AssemblyVersion`|選擇性 `String` 參數。<br /><br /> 為已產生的資訊清單指定組件識別的 `Version` 欄位。  如果沒有指定此參數，便會使用 "1.0.0.0" 的預設值。|  
|`ClrVersion`|選擇性 `String` 參數。<br /><br /> 指定應用程式所需的最小 Common Language Runtime \(CLR\) 版本。  預設值是建置系統使用的 CLR 版本。  如果工作是要產生原生資訊清單，即忽略此參數。|  
|`ConfigFile`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含應用程式組態檔的項目。  如果工作是要產生原生資訊清單，即忽略此參數。|  
|`Dependencies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定項目清單，為產生的資訊清單定義相依組件集。  每個項目可以利用項目中繼資料 \(Metadata\) 進一步描述，以指出其他部署狀態和相依性的類型。  如需詳細資訊，請參閱以下的＜項目中繼資料＞一節。|  
|`Description`|選擇性 `String` 參數。<br /><br /> 指定應用程式或元件的描述。|  
|`EntryPoint`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定單一項目，指出產生的資訊清單組件的進入點。<br /><br /> 對於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單，這個參數指定在應用程式執行時啟動的組件。|  
|`ErrorReportUrl`|選擇性 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 參數。<br /><br /> 指定在報告 ClickOnce 安裝中的錯誤時顯示於對話方塊中的網頁 URL。|  
|`FileAssociations`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定與 ClickOnce 部署資訊清單相關聯之一個或多個檔案類型的清單。<br /><br /> 檔案關聯只有在 .NET Framework 3.5 \(含\) 以後版本做為目標時才有效。|  
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要併入資訊清單的檔案。  指定每個檔案的完整路徑。|  
|`HostInBrowser`|選擇性 [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 參數。<br /><br /> 如果為 `true`，表示應用程式是裝載於瀏覽器中 \(與 WPF Web 瀏覽器應用程式相同\)。|  
|`IconFile`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 表示應用程式圖示檔。  應用程式圖示會在產生的應用程式資訊清單中顯示，並在「開始」功能表和「新增或移除程式」對話方塊中使用。  如果沒有指定這項輸入，便會使用預設圖示。  如果工作是要產生原生資訊清單，即忽略此參數。|  
|`InputManifest`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 表示輸入 XML 文件，做為資訊清單產生器的基底。  這讓像是應用程式安全性或自訂資訊清單定義的結構化資料，能夠反映在輸出資訊清單中。  XML 文件中的根項目 \(Root Element\) 必須是 asmv1 命名空間中的組件節點。|  
|`IsolatedComReferences`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要在產生的資訊清單中隔離的 COM 元件。  這個參數支援可在「免註冊的 COM」部署中隔離 COM 元件的功能。  利用標準的 COM 註冊定義來自動產生資訊清單之後，就可以達到隔離的效果。  不過，COM 元件必須在建置電腦上註冊，才能讓這項功能正常運作。|  
|`ManifestType`|選擇性 `String` 參數。<br /><br /> 指定要產生的資訊清單類型。  這個參數可能具有下列其中一個值：<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> 如果沒有指定此參數，工作便會預設為 `ClickOnce`。|  
|`MaxTargetPath`|選擇性 `String` 參數。<br /><br /> 指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署中檔案路徑允許的長度上限。  如果有指定此值，就會依據這項限制檢查應用程式中每個檔案路徑的長度。  超過限制的任何項目都會引發建置警告。  如果未指定此輸入或其值為零，就不會執行任何檢查。  如果工作是要產生原生資訊清單，即忽略此參數。|  
|`OSVersion`|選擇性 `String` 參數。<br /><br /> 指定應用程式所需的最小作業系統 \(OS\) 版本。  例如，"5.1.2600.0" 的值表示作業系統是 Windows XP。  如果沒有指定此參數，便會使用表示 Windows 98 Second Edition 的 "4.10.0.0"，也就是 .NET Framework 支援的最小 OS 版本。  如果工作是要產生原生資訊清單，便會忽略這項輸入。|  
|`OutputManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定產生之輸出資訊清單檔的名稱。  如果未指定此參數，就會從產生的資訊清單之識別中推斷輸出檔的名稱。|  
|`Platform`|選擇性 `String` 參數。<br /><br /> 指定應用程式的目標平台。  這個參數可能具有下列其中一個值：<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 如果沒有指定此參數，工作便會預設為 `AnyCPU`。|  
|`Product`|選擇性 `String` 參數。<br /><br /> 指定應用程式的名稱。  如果未指定此參數，就會從產生資訊清單的識別推斷名稱。  此名稱用於 \[開始\] 功能表上的捷徑名稱，而且是出現在 \[新增或移除程式\] 對話方塊中名稱的一部分。|  
|`Publisher`|選擇性 `String` 參數。<br /><br /> 指定應用程式的發行者。  如果未指定此參數，就會從註冊的使用者，或是產生資訊清單的識別推斷名稱。  此名稱用於 \[開始\] 功能表上的資料夾名稱，而且是出現在 \[新增或移除程式\] 對話方塊中名稱的一部分。|  
|`RequiresMinimumFramework35SP1`|選擇性 `Boolean` 參數。<br /><br /> 如果為 true，則應用程式需要 .NET Framework 3.5 SP1 或更新的版本。|  
|`TargetCulture`|選擇性 `String` 參數。<br /><br /> 識別應用程式的文化特性 \(Culture\)，並指定產生資訊清單之組件識別的 `Language` 欄位。  如果未指定此參數，就會假設應用程式不因文化特性而異。|  
|`TargetFrameworkMoniker`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定目標 Framework Moniker。|  
|`TargetFrameworkProfile`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定目標 Framework 設定檔。|  
|`TargetFrameworkSubset`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定要做為目標之 .NET Framework 子集的名稱。|  
|`TargetFrameworkVersion`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定專案的目標 .NET Framework。|  
|`TrustInfoFile`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 表示指定應用程式安全性的 XML 文件。  XML 文件中的根項目必須是 asmv2 命名空間中的 trustInfo 節點。  如果工作是要產生原生資訊清單，即忽略此參數。|  
|`UseApplicationTrust`|選擇性 assetId:///Boolean?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 如果為 true，則會將 `Product`、`Publisher` 和 `SupportUrl` 屬性寫入應用程式資訊清單中。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需 Task 類別的參數清單，請參閱 [Task Base Class](../msbuild/task-base-class.md)。  
  
 如需如何使用 `GenerateDeploymentManifest` 工作的詳細資訊，請參閱[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)。  
  
 相依性和檔案的輸入可以進一步用項目中繼資料裝飾，以指定每個項目的其他部署狀態。  
  
## 項目中繼資料  
  
|中繼資料名稱|描述|  
|------------|--------|  
|`DependencyType`|指出相依性是以應用程式或必要條件進行發行和安裝。  這項中繼資料可用於所有的相依性，但不能用於檔案。  此中繼資料可用的值如下：<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install 是預設值。|  
|`AssemblyType`|指出相依性為 Managed 或原生組件。  這項中繼資料可用於所有的相依性，但不能用於檔案。  此中繼資料可用的值如下：<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` 是預設值，表示資訊清單產生器將會自動決定組件類型。|  
|`Group`|表示視需要下載額外檔案的群組。  群組名稱是由應用程式定義，並且可以是任何字串。  預設的空字串表示檔案不是下載群組的一部分。  不在群組中的檔案都是初始應用程式下載的一部分。  群組中的檔案只會在應用程式使用 <xref:System.Deployment.Application> 明確要求時下載。<br /><br /> 這項中繼資料可用於 `IsDataFile` 為 `false` 的所有檔案，以及 `DependencyType` 為 `Install` 的所有相依性。|  
|`TargetPath`|指定應該如何在產生的資訊清單中定義路徑。  這個屬性 \(Attribute\) 可用於所有檔案。  如果沒有指定此屬性，便會使用項目規格。  這個屬性可用於 `DependencyType` 值為 `Install` 的所有檔案和相依性。|  
|`IsDataFile`|`Boolean` 中繼資料值，指出檔案是否為資料檔案。  資料檔的特殊性在於會在應用程式更新之間移轉。  這項中繼資料只可用於檔案。  `False` 是預設值。|  
  
## 範例  
 這個範例使用 `GenerateApplicationManifest` 工作來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單，並用 `GenerateDeploymentManifest` 工作來為具有單一組件的應用程式產生部署資訊清單。  然後再使用 `SignFile` 工作為資訊清單簽章。  
  
 上述範例說明了產生資訊清單時可能發生的最簡單案例，其中 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單是針對單一程式而產生的。  預設名稱和識別都從資訊清單的組件推斷而來。  
  
> [!NOTE]
>  在以下範例中，所有應用程式二進位碼檔案都是預先建置，以便專注於資訊清單產生的各方面。  這個範例會產生能夠完整運作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  如需本範例 `SignFile` 工作中所使用 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile Task](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 範例  
 這個範例使用 `GenerateApplicationManifest` 和 `GenerateDeploymentManifest` 工作來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，以及具有單一組件的應用程式的部署資訊清單，並指定資訊清單的名稱和識別。  
  
 除了明確指定資訊清單的名稱和識別以外，這個範例與前一個範例相類似。  此外，這個範例被設定為線上應用程式，而非安裝的應用程式。  
  
> [!NOTE]
>  在以下範例中，所有應用程式二進位碼檔案都是預先建置，以便專注於資訊清單產生的各方面。  這個範例會產生能夠完整運作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  如需本範例 `SignFile` 工作中所使用 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile Task](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 範例  
 這個範例使用 `GenerateApplicationManifest` 和 `GenerateDeploymentManifest` 工作來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，以及具有多個檔案和組件的應用程式的部署資訊清單。  
  
> [!NOTE]
>  在以下範例中，所有應用程式二進位碼檔案都是預先建置，以便專注於資訊清單產生的各方面。  這個範例會產生能夠完整運作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
> [!NOTE]
>  如需本範例 `SignFile` 工作中所使用 `Thumbprint` 屬性的詳細資訊，請參閱 [SignFile Task](../msbuild/signfile-task.md)。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## 範例  
 這個範例使用 `GenerateApplicationManifest` 工作來產生應用程式 Test.exe 的原生資訊清單，並參考原生元件 Alpha.dll 和隔離的 COM 元件 Bravo.dll。  
  
 這個範例產生 Test.exe.manifest，使應用程式 XCOPY 能夠利用「免註冊的 COM」進行部署。  
  
> [!NOTE]
>  在以下範例中，所有應用程式二進位碼檔案都是預先建置，以便專注於資訊清單產生的各方面。  這個範例會產生能夠完整運作的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile Task](../msbuild/signfile-task.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)