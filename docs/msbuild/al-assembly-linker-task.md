---
title: "AL (Assembly Linker) Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AL task [MSBuild]"
  - "MSBuild, AL task"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AL (Assembly Linker) Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

AL 工作會包裝 AL.exe，這是隨附 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 一起散發的工具。  「組件連結器」工具會從一或多個檔案 \(模組或資源檔\)，以資訊清單建立組件。  編譯器 \(Compiler\) 和開發環境可能已經提供這些功能，因此通常不需要直接使用這項工作。  開發人員若要從多個元件檔案建立一個組件，例如，混合語言開發時產生的多個元件檔案，組件連結器是再適合不過的了。  這項工作不會將模組結合為單一組件檔，因為必須要能夠散發和使用個別的模組，才能正確載入結果組件。  如需 AL.exe 的詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)。  
  
## 參數  
 下表說明 `AL` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AlgorithmID`|選擇性 `String` 參數。<br /><br /> 指定雜湊多檔案組件中所有檔案 \(除了包含組件資訊清單的檔案之外\) 的演算法。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/algid` 選項的文件。|  
|`BaseAddress`|選擇性 `String` 參數。<br /><br /> 指定在執行階段將 DLL 載入使用者電腦上的位址。  如果指定 DLL 的基底位址 \(Base Address\)，而不是由作業系統重新找出處理空間中的 DLL，應用程式載入的速度會較快。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的  \/base\[address\] 選項。|  
|`CompanyName`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Company` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/comp[any]` 選項的文件。|  
|`Configuration`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Configuration` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/config[uration]` 選項的文件。|  
|`Copyright`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Copyright` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/copy[right]` 選項的文件。|  
|`Culture`|選擇性 `String` 參數。<br /><br /> 指定與組件關聯的文化特性 \(Culture\) 字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/c[ulture]` 選項的文件。|  
|`DelaySign`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則只將公開金鑰 \(Public Key\) 置於組件中；如果為 `false`，則對組件完整簽章。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/delay[sign]` 選項的文件。|  
|`Description`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Description` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/descr[iption]` 選項的文件。|  
|`EmbedResources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在含有組件資訊清單的影像中內嵌指定的資源。  這項工作將資源檔中的內容複製到影像中。  傳入此參數的項目中可能含有附加的選擇性中繼資料 \(Metadata\)，稱為 `LogicalName` 和 `Access`。  `LogicalName` 中繼資料的用途為指定資源的內部識別項。  `Access` 中繼資料可以設定為 `private`，避免其他組件資源看到這項資源。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/embed[resource]` 選項的文件。|  
|`EvidenceFile`|選擇性 `String` 參數。<br /><br /> 以 `Security.Evidence` 的資源名稱將指定的檔案內嵌在組件中。<br /><br /> `Security.Evidence` 不可用於標準資源。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/e[vidence]` 選項。|  
|`ExitCode`|選擇性 \(Optional\) `Int32` 輸出唯讀參數。<br /><br /> 指定由執行的命令所提供的結束代碼 \(Exit Code\)。|  
|`FileVersion`|選擇性 `String` 參數。<br /><br /> 為組件中的 `File Version` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/fileversion` 選項的文件。|  
|`Flags`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Flags` 欄位指定值。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/flags` 選項的文件。|  
|`GenerateFullPaths`|選擇性 `Boolean` 參數。<br /><br /> 使工作針對錯誤訊息中報告的任何檔案使用絕對路徑。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/fullpaths` 選項。|  
|`KeyContainer`|選擇性 `String` 參數。<br /><br /> 指定保留金鑰組的容器。  這將會藉由將公開金鑰插入組件資訊清單中來簽署組件 \(為它指定強式名稱\)。  然後工作將會使用私密金鑰為最後的組件簽署。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/keyn[ame]` 選項的文件。|  
|`KeyFile`|選擇性 `String` 參數。<br /><br /> 指定含有金鑰組 \(Key Pair\) 的檔案，或是只要指定公開金鑰，來為組件簽署。  編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最後的組件。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/keyf[ile]` 選項的文件。|  
|`LinkResources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將指定的資源檔連結至組件。  資源會成為組件的一部分，不過不會複製檔案。  傳入此參數的項目中可能含有附加的選擇性中繼資料，稱為 `LogicalName`、`Target` 和 `Access`。  `LogicalName` 中繼資料的用途為指定資源的內部識別項。  `Target` 中繼資料可以指定工作將檔案複製到的路徑和檔名，在此之後便將此新檔編譯至組件中。  `Access` 中繼資料可以設定為 `private`，避免其他組件資源看到這項資源。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/link[resource]` 選項的文件。|  
|`MainEntryPoint`|選擇性 `String` 參數。<br /><br /> 指定將模組轉換成可執行檔時，用來做為進入點 \(Entry Point\) 之方法的完整名稱 \(*class.method*\)。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/main` 選項。|  
|`OutputAssembly`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定由此工作產生的檔案名稱。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/out` 選項。|  
|`Platform`|選擇性 `String` 參數。<br /><br /> 限制此程式碼可執行的平台，必須是其中一個 `x86`、`Itanium`、`x64` 或 `anycpu`。  預設值為 `anycpu`。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/platform` 選項。|  
|`ProductName`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Product` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/prod[uct]` 選項的文件。|  
|`ProductVersion`|選擇性 `String` 參數。<br /><br /> 為組件中的 `ProductVersion` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/productv[ersion]` 選項的文件。|  
|`ResponseFiles`|選擇性 `String[]` 參數。<br /><br /> 指定含有其他選項的回應檔 \(Response File\) 以傳遞至組件連結器。|  
|`SdkToolsPath`|選擇性 `String` 參數。<br /><br /> 指定 SDK 工具 \(例如 resgen.exe\) 的路徑。|  
|`SourceModules`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要編譯至組件中的一或多個模組。  模組將會列示在結果組件的資訊清單中，而且依然需要散發和提供使用，才能載入組件。  傳入此參數的項目中可能含有稱為 `Target` 的其他中繼資料，指定工作將檔案複製到的路徑和檔名，在此之後便會將此新檔編譯到組件中。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 的文件。  這個參數對應於傳入 Al.exe 的模組清單 \(不含特定的參數\)。|  
|`TargetType`|選擇性 `String` 參數。<br /><br /> 指定輸出檔的檔案格式：`library` \(程式碼程式庫\)、`exe` \(主控台應用程式\) 或 `win` \(Windows 架構應用程式\)。  預設值為 `library`。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/t[arget]` 選項。|  
|`TemplateFile`|選擇性 `String` 參數。<br /><br /> 指定要從其中繼承所有組件中繼資料 \(文化特性 \(Culture\) 欄位除外\) 的組件。  指定的組件必須具有強式名稱 \(Strong Name\)。<br /><br /> 使用 `TemplateFile` 參數建立的組件將會是附屬組件。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/template` 選項。|  
|`Timeout`|選擇性 `Int32` 參數。<br /><br /> 指定以毫秒為單位的時間長度，這段時間過後即結束工作可執行檔。  預設值為 `Int.MaxValue`，表示沒有逾時時間。|  
|`Title`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Title` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/title` 選項的文件。|  
|`ToolPath`|選擇性 `String` 參數。<br /><br /> 指定工作將會載入基礎可執行檔 \(Al.exe\) 的位置。  如果未指定此參數，工作會使用對應於執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 之架構版本的 SDK 安裝路徑。|  
|`Trademark`|選擇性 `String` 參數。<br /><br /> 為組件中的 `Trademark` 欄位指定字串。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/trade[mark]` 選項的文件。|  
|`Version`|選擇性 `String` 參數。<br /><br /> 指定這個組件的版本資訊。  此字串的格式為 *major.minor.build.revision*。  預設值為 0。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/v[ersion]` 選項的文件。|  
|`Win32Icon`|選擇性 `String` 參數。<br /><br /> 將 .ico 檔案插入組件中。  將.ico檔讓輸出檔具有在檔案總管中所需的外觀。  這個參數對應於[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中的 `/win32icon` 選項。|  
|`Win32Resource`|選擇性 `String` 參數。<br /><br /> 將 Win32 資源 \(.res 檔案\) 插入輸出檔案中。  如需詳細資訊，請參閱[Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) 中之 `/win32res` 選項的文件。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)。  
  
## 範例  
 下列範例以指定的選項建立組件。  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)