---
title: "建立軟體開發套件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1d5ea891137bff643ebfcb67cd739aefeb74c2df
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-software-development-kit"></a>建立軟體開發套件
軟體開發套件 (SDK) 是 Api，您可以在 Visual Studio 中的單一項目參考的集合。 **參考管理員**對話方塊會列出所有與專案相關的 Sdk。 SDK 加入至專案時，就使用 Visual Studio 中的 Api。  
  
 有兩種類型的 Sdk:  
  
-   平台 Sdk 是開發平台的應用程式的必要元件。 例如， [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK，才能開發[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  
  
-   擴充功能 Sdk 是擴充平台，但不是強制性的開發平台的應用程式的選用元件。  
  
 下列章節說明 Sdk 以及如何建立 platform SDK 的一般基礎結構和擴充功能 SDK。  
  
-   [平台 Sdk](#PlatformSDKs)  
  
-   [擴充功能 Sdk](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a>平台 Sdk  
 平台 Sdk，才能開發平台的應用程式。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]開發的應用程式必須有 SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]。  
  
### <a name="installation"></a>安裝  
 所有平台 Sdk 將會安裝在 HKLM\Software\Microsoft\Microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK root]。 因此， [!INCLUDE[win81](../debugger/includes/win81_md.md)] HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 在已安裝的 SDK。  
  
### <a name="layout"></a>版面配置  
 平台 Sdk 將會有下列配置︰  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|節點|說明|  
|----------|-----------------|  
|[參考] 資料夾|包含二進位檔，包含可以比照的 Api。 這些可能包括 Windows 中繼資料 (WinMD) 檔案或組件。|  
|DesignTime 資料夾|包含僅在前-run/偵錯階段所需的檔案。 這些可能包括 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等<br /><br /> XML 文件，理論上，放在 \DesignTime 資料夾中，但 XML 文件的參考會繼續被放置在一起的 Visual Studio 中的參考檔案。 例如，XML 文件的參考 \References\\[組態]\\[arch]\sample.dll 會 \References\\[組態]\\[arch]\sample.xml，而且該文件的當地語系化的版本都 \References\\[組態]\\[架構]\\[locale]\sample.xml。|  
|設定資料夾|可以是只有三個資料夾︰ 偵錯、 零售和 CommonConfiguration。 如果同一組 SDK 檔案應該取用，不論 SDK 取用者將做為目標的組態，SDK 作者可以將放置在 CommonConfiguration 檔案。|  
|架構資料夾|有任何支援的架構資料夾。 Visual Studio 支援下列架構︰ x86、 x64、 ARM 和中性。 注意︰ Win32 對應到 x86，而 AnyCPU 對應至中性。<br /><br /> 平台 Sdk 下 \CommonConfiguration\neutral 只會尋找 MSBuild。|  
|SDKManifest.xml|此檔案描述 Visual Studio 使用 SDK 的方式。 看看 SDK 資訊清單[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **顯示名稱︰**物件瀏覽器會顯示在瀏覽清單中的值。<br /><br /> **PlatformIdentity:**是否存在，這個屬性會告知 Visual Studio 和 MSBuild SDK 是平台 SDK 和從它所加入的參考，不應該複製在本機。<br /><br /> **TargetFramework:** Visual Studio 會使用這個屬性以確保，只有專案中的值所指定相同的架構為目標屬性可以使用 SDK。<br /><br /> **MinVSVersion:** Visual Studio 會使用這個屬性使用套用至該 Sdk。<br /><br /> **參考︰**這個屬性必須指定為僅包含控制項的參考。 如需如何指定參考是否包含的控制項，如下所示。|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a>擴充功能 Sdk  
 下列各節說明您要如何部署擴充功能 SDK。  
  
### <a name="installation"></a>安裝  
 擴充功能 Sdk 可以為特定使用者，或是針對所有使用者安裝但未指定登錄機碼。 若要安裝 SDK，針對所有使用者，請使用下列路徑︰  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 使用者特定的安裝，請使用下列路徑︰  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 如果您想要使用不同的位置，您必須執行下列其中一種︰  
  
1.  在登錄機碼中指定︰  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     新增的值為 （預設值） 子機碼和`<path to SDK><SDKName><SDKVersion>`。  
  
2.  將 MSBuild 屬性加入`SDKReferenceDirectoryRoot`專案檔。 這個屬性的值是位於您想要參考的擴充功能 Sdk 的目錄半冒號分隔清單。  
  
### <a name="installation-layout"></a>安裝配置  
 擴充功能 Sdk 有下列安裝配置︰  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\<>\>\\<>\>︰ 名稱和版本的 SDK SDK 根衍生自對應的資料夾名稱的路徑中的延伸模組。 MSBuild 會使用這個身分識別在磁碟上，在此找到 SDK 和 Visual Studio 會顯示在這個身分識別**屬性**視窗和**參考管理員** 對話方塊。  
  
2.  [參考] 資料夾︰ 包含 Api 的二進位檔。 這可能是 Windows 中繼資料 (WinMD) 檔案或組件。  
  
3.  可轉散發套件資料夾︰ 所需的執行階段/偵錯及使用者的應用程式的一部分應該取得封裝的檔案。 所有的二進位檔應該放下方 \redist\\<>\>\\<>\>，和二進位檔的名稱應該具有下列格式來確保唯一性︰ **\<公司 >。\<產品 >。\<用途 >。\<extension>**. 例如，Microsoft.Cpp.Build.dll。 與其他 sdk （例如 javascript、 css、 pri、 xaml、 png 和 jpg 檔案） 的檔案名稱的名稱可能會發生衝突的所有檔案應該都置於下方 \redist\\<>\>\\<>\>\\<>\>\ XAML 相關聯的檔案除外控制。 這些檔案應該置於下方 \redist\\<>\>\\<>\>\\<>\>\\。  
  
4.  DesignTime 資料夾︰ 檔案所需的唯一前-run/偵錯的時間，且不應該封裝使用者的應用程式的一部分。 這些可能是 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等。 適用於使用原生專案所必須擁有任何 SDK *SDKName*.props 檔案。 下圖顯示這種檔案類型的範例。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML 參考文件會放置在一起的參考檔案。 例如，XML 參考文件**\References\\<>\>\\<>\>\sample.dll**組件是**\References\\<>\>\\<>\>\sample.xml**，該文件的當地語系化的版本，而且**\References\\<>\>\\<>\>\\<>\>\sample.xml**。  
  
5.  設定資料夾︰ 三個子資料夾︰ 偵錯、 零售和 CommonConfiguration。 同一組 SDK 檔案應該取用，不論目標 SDK 取用者的組態時，SDK 作者可以放置在 CommonConfiguration 檔案。  
  
6.  架構資料夾︰ 支援下列架構︰ x86、 x64、 ARM、 中性。 Win32 對應到 x86，而 AnyCPU 對應至中性。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 此檔案描述 Visual Studio 使用 SDK 的方式。 下列為範例。  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 下列清單提供檔案的項目。  
  
1.  顯示名稱︰ 值，這個值會出現在 [參考管理員]、 [方案總管]、 物件瀏覽器和 Visual Studio 使用者介面中的其他位置。  
  
2.  ProductFamilyName︰ 整體 SDK 產品名稱。 例如， [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK 名為 「 Microsoft.WinJS.1.0 」 和 「 Microsoft.WinJS.2.0 」，屬於相同系列的 SDK 產品系列，「 Microsoft.WinJS 」。 此屬性可讓 Visual Studio 和 MSBuild 建立該連線。 如果這個屬性不存在，SDK 名稱將作為該產品系列名稱。  
  
3.  FrameworkIdentity︰ 指定這個屬性的值會放入取用應用程式資訊清單的一個或多個 Windows 元件庫相依性。 這是屬性只適用於 Windows 元件程式庫。  
  
4.  TargetFramework︰ 指定可在 [參考管理員] 和 [工具箱] 的 Sdk。 這是以分號分隔的清單目標 framework moniker，例如 「.NET Framework，version = v2.0;.NET Framework、 版本 = v4.5.1 」。 如果指定了數個相同的目標架構版本，參考管理員會使用指定最低的版本進行篩選。 比方說，如果 「.NET Framework、 版本 = v2.0;.NET Framework、 版本 = v4.5.1"指定，則會使用參考管理員 「.NET Framework、 版本 = v2.0 」。 如果指定的特定目標 framework 設定檔，則該設定檔將會使用參考管理員進行篩選。 例如，當 「 Silverlight，版本 = v4.0，profile = WindowsPhone"指定，則參考管理員 的篩選，只有 Windows Phone 設定檔。以完整的 Silverlight 4.0 Framework 為目標的專案不會看到 SDK 參考管理員。  
  
5.  MinVSVersion: 最小 Visual Studio 版本。  
  
6.  MaxPlatformVerson︰ 最大的目標平台版本應該用來指定擴充功能 SDK 將無法運作所在的平台版本。 例如，Microsoft Visual c + + 執行階段套件 v11.0 應該參考只能由 Windows 8 專案。 因此，Windows 8 專案 MaxPlatformVersion 是 8.0。 也就是說，對於 Windows 8.1 專案，[參考管理員] 會篩選掉 Microsoft Visual c + + 執行階段套件，MSBuild 會擲回錯誤時[!INCLUDE[win81](../debugger/includes/win81_md.md)]專案參考它。 注意︰ 此項目從支援[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。  
  
7.  AppliesTo︰ 指定的 Sdk，可在 參考管理員藉由指定適用的 Visual Studio 專案類型。 可辨識的九個值︰ WindowsAppContainer、 VisualC、 VB、 CSharp、 WindowsXAML、 JavaScript、 受管理和原生。 SDK 作者可以使用和 ("+')，或 ("|")，而非 (」 ！ 」)若要指定完全適用於 SDK 的專案類型的範圍運算子。  
  
     WindowsAppContainer 識別專案[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  
  
8.  SupportPrefer32Bit︰ 支援的值為"True"和"False"。 預設值為"True"。 如果值設定為"False"，MSBuild 會傳回錯誤[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]專案 （或警告的桌面專案） 參考 SDK 的專案是否啟用 Prefer32Bit。 如需 Prefer32Bit 的詳細資訊，請參閱[建置專案設計工具、 頁 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[編譯的頁面上，專案設計工具 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)。  
  
9. SupportedArchitectures︰ 以分號分隔的清單的 SDK 支援的架構。 如果不支援目標的 SDK 架構中使用的專案，MSBuild 會顯示警告。 如果未指定此屬性，MSBuild 會永遠不會顯示這種類型的警告。  
  
10. SupportsMultipleVersions︰ 如果此屬性設為**錯誤**或**警告**，MSBuild 會指出相同的專案無法參考多個版本的相同 SDK 系列。 如果這個屬性不存在，或設為**允許**，MSBuild 不會顯示這種類型的錯誤或警告。  
  
11. AppX︰ 指定磁碟上的 Windows 元件程式庫的應用程式套件的路徑。 在本機偵錯期間，這個值會傳遞給 Windows 元件程式庫的註冊元件。 檔案名稱的命名慣例是**\<公司 >。\<產品 >。\<架構 >。\<組態 >。\<版本 >.appx**。 設定與架構是選擇性的屬性名稱和屬性值，如果它們並未套用至 Windows 元件庫。 這個值是僅適用於 Windows 元件程式庫。  
  
12. CopyRedistToSubDirectory︰ 指定相對於應用程式封裝根目錄 \redist 資料夾下的檔案應該複製 (也就是**封裝位置**選擇建立應用程式套件精靈 中) 和執行階段配置根。 預設位置是應用程式套件和 F5 配置的根。  
  
13. DependsOn︰ 定義此 SDK 取決於 Sdk 的 SDK 身分清單。 這個屬性會出現在詳細資料窗格的 [參考管理員] 中。  
  
14. MoreInfo︰ 提供說明和詳細資訊的網頁 URL。 在右窗格的 [參考管理員] 中的其他相關資訊連結，會使用此值。  
  
15. 註冊類型︰ 指定 WinMD 註冊應用程式資訊清單中，而且需要其對應項目實作 DLL 的原生 winmd。  
  
16. 檔案的參考︰ 指定包含控制項或原生 Winmd 這些參考。 如何指定參考是否包含控制項的相關資訊，請參閱[指定工具箱項目的位置](#ToolboxItems)下方。  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>指定工具箱項目的位置  
 ToolBoxItems SDKManifest.xml 結構描述項目會指定平台和擴充功能 Sdk 中的類別和工具箱項目的位置。 下列範例示範如何指定不同的位置。 這是適用於 WinMD 或 DLL 的參考。  
  
1.  將控制項置於工具箱預設分類。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  將控制項以特定類別的名稱。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  放置在特定的類別名稱 底下的控制項。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  在 Blend 和 Visual Studio 中放置在不同的類別名稱 底下的控制項。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  列舉不同的 Blend 和 Visual Studio 的特定控制項。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  列舉特定控制項，並將它們放在 Visual Studio 常見路徑，或只存在於所有的控制項群組。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  列舉特定控制項，並顯示特定集合中 ChooseItems，不加括號會出現在 [工具箱]。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 建立使用 c + + 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說︰ 建立使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [管理專案中的參考](../ide/managing-references-in-a-project.md)
