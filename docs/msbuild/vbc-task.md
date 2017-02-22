---
title: "Vbc Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Vbc task [MSBuild]"
  - "MSBuild, Vbc task"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vbc Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 vbc.exe，產生可執行檔 \(.exe\)、動態連結程式庫 \(.dll\) 或程式碼模組 \(.  netmodule\)。  如需 vbc.exe 的詳細資訊，請參閱 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)。  
  
## 參數  
 下表說明 `Vbc` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AdditionalLibPaths`|選擇性 `String[]` 參數。<br /><br /> 指定其他資料夾，以便在其中尋找 References 屬性 \(Attribute\) 中指定的組件。|  
|`AddModules`|選擇性 `String[]` 參數。<br /><br /> 讓編譯器允許您目前正在編譯的專案使用指定檔案中的所有型別資訊。  這個參數 \(Parameter\) 對應於 vbc.exe 編譯器的 [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) 參數 \(Switch\)。|  
|`BaseAddress`|選擇性 `String` 參數。<br /><br /> 指定 DLL 的基底位址 \(Base Address\)。  這個參數 \(Parameter\) 對應於 vbc.exe 編譯器的 [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) 參數 \(Switch\)。|  
|`CodePage`|選擇性 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。  這個參數對應於 vbc.exe 編譯器的 [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) 參數。|  
|`DebugType`|選擇性 `String[]` 參數。<br /><br /> 使編譯器產生偵錯資訊。  這個參數可能具有下列其中一個值：<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 預設值為 `full`，對執行的程式附加偵錯工具。  `pdbonly` 值讓程式在偵錯工具中啟動時進行原始程式碼偵錯，但是如果執行的程式是附加至偵錯工具，就只會顯示組合語言碼。  如需詳細資訊，請參閱 [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|`DefineConstants`|選擇性 `String[]` 參數。<br /><br /> 定義條件式編譯器常數。  Symbol\/value 配對通常由分號來分隔，並以下列語法指定：<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 這個參數對應於 vbc.exe 編譯器的 [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) 參數。|  
|`DelaySign`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，工作便會將公開金鑰 \(Public Key\) 置於組件中。  如果為 `false`，工作便會對組件完整簽章。  預設值為 `false`。除非搭配 `KeyFile` 參數或 `KeyContainer` 參數使用，否則這個參數不具有任何效果。  這個參數對應於 vbc.exe 編譯器的 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) 參數。|  
|`DisabledWarnings`|選擇性 `String` 參數。<br /><br /> 隱藏指定的警告。  您只需要指定警告識別項的數字部分。  分號會分隔多個警告。  這個參數對應於 vbc.exe 編譯器的 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 參數。|  
|`DocumentationFile`|選擇性 `String` 參數。<br /><br /> 將文件註解處理至指定的 XML 檔案。  這個參數會覆寫 `GenerateDocumentation` 屬性。  如需詳細資訊，請參閱 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。|  
|`EmitDebugInformation`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，工作便會產生偵錯資訊並將之置於 .pdb 檔中。  如需詳細資訊，請參閱 [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|`ErrorReport`|選擇性 `String` 參數。<br /><br /> 指定工作報告編譯器內部錯誤的方式。  這個參數可能具有下列其中一個值：<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> 如果指定 `prompt`，當發生編譯器內部錯誤時，就會提示使用者選擇是否將錯誤資料傳送至 Microsoft。<br /><br /> 如果指定 `send`，當發生編譯器內部錯誤時，工作便會將錯誤資料傳送至 Microsoft。<br /><br /> 預設值為 `none`，只以文字輸出來報告錯誤。<br /><br /> 這個參數對應於 vbc.exe 編譯器的 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) 參數。|  
|`FileAlignment`|選擇性 `Int32` 參數。<br /><br /> 指定要對齊輸出檔案區段的位置 \(以位元組為單位\)。  這個參數可能具有下列其中一個值：<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 這個參數對應於 vbc.exe 編譯器的 [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) 參數。|  
|`GenerateDocumentation`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則會產生文件資訊並將之置於 XML 檔中 \(依照工作正在建立的可執行檔或程式庫來命名\)。  如需詳細資訊，請參閱 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。|  
|`Imports`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 從指定的項目集合中匯入命名空間。  這個參數對應於 vbc.exe 編譯器的 [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) 參數。|  
|`KeyContainer`|選擇性 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。  這個參數對應於 vbc.exe 編譯器的 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) 參數。|  
|`KeyFile`|選擇性 `String` 參數。<br /><br /> 指定含有密碼編譯金鑰的檔案名稱。  如需詳細資訊，請參閱 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)。|  
|`LangVersion`|選擇性 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 參數。<br /><br /> 指定語言版本 \("9" 或 "10"\)。|  
|`LinkResources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 .NET Framework 資源的連結；資源檔並非置於輸出檔中。  這個參數對應於 vbc.exe 編譯器的 [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) 參數。|  
|`MainEntryPoint`|選擇性 `String` 參數。<br /><br /> 指定包含 `Sub Main` 程序的類別或模組。  這個參數對應於 vbc.exe 編譯器的 [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) 參數。|  
|`ModuleAssemblyName`|選擇性 `String` 參數。<br /><br /> 指定此模組所屬的組件。|  
|`NoConfig`|選擇性 `Boolean` 參數。<br /><br /> 指定編譯器不應該使用 vbc.rsp 檔。  這個參數對應於 vbc.exe 編譯器的 [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) 參數。|  
|`NoLogo`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則隱藏編譯器橫幅資訊的顯示。  這個參數對應於 vbc.exe 編譯器的 [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) 參數。|  
|`NoStandardLib`|選擇性 `Boolean` 參數。<br /><br /> 導致編譯器不參考標準程式庫。  這個參數對應於 vbc.exe 編譯器的 [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) 參數。|  
|`NoVBRuntimeReference`|選擇性 `Boolean` 參數。<br /><br /> 僅限內部使用。  如果為 true，則阻止 Microsoft.VisualBasic.dll 的自動參考。|  
|`NoWarnings`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，工作便會隱藏所有警告。  如需詳細資訊，請參閱 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。|  
|`Optimize`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則啟用編譯器最佳化。  這個參數對應於 vbc.exe 編譯器的 [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) 參數。|  
|`OptionCompare`|選擇性 `String` 參數。<br /><br /> 指定如何進行字串比較。  這個參數可能具有下列其中一個值：<br /><br /> -   `binary`<br />-   `text`<br /><br /> `binary` 值會指定工作使用二進位字串比較。  `text` 值指定工作使用文字字串比較。  此參數的預設值為 `binary`。  這個參數對應於 vbc.exe 編譯器的 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) 參數。|  
|`OptionExplicit`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則必須明確宣告變數。  這個參數對應於 vbc.exe 編譯器的 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) 參數。|  
|`OptionInfer`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則允許變數的型別推斷。|  
|`OptionStrict`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，工作便會強制嚴格型別語意以限制隱含型別轉換。  這個參數對應於 vbc.exe 編譯器的 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 參數。|  
|`OptionStrictType`|選擇性 `String` 參數。<br /><br /> 指定哪些嚴格型別語義產生警告。  目前僅支援 "custom"。  這個參數對應於 vbc.exe 編譯器的 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 參數。|  
|`OutputAssembly`|選擇性 `String` 輸出參數。<br /><br /> 指定輸出檔的名稱。  這個參數對應於 vbc.exe 編譯器的 [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) 參數。|  
|`Platform`|選擇性 `String` 參數。<br /><br /> 指定做為輸出檔目標的處理器平台。  這個參數可以具有 `x86`、`x64`、`Itanium` 或 `anycpu` 值。  預設值為 `anycpu`。  這個參數對應於 vbc.exe 編譯器的 [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) 參數。|  
|`References`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 使工作從指定的項目將公用型別資訊匯入到目前的專案。  這個參數對應於 vbc.exe 編譯器的 [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) 參數。|  
|`RemoveIntegerChecks`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則停用整數的溢位錯誤檢查。  預設值是 `false`。  這個參數對應於 vbc.exe 編譯器的 [\/removeintcheck](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) 參數。|  
|`Resources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 .NET Framework 資源嵌入輸出檔。  這個參數對應於 vbc.exe 編譯器的 [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) 參數。|  
|`ResponseFiles`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定含有這個工作命令的回應檔 \(Response File\)。  這個參數對應於 vbc.exe 編譯器的 [@ \(Specify Response File\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) 選項。|  
|`RootNamespace`|選擇性 `String` 參數。<br /><br /> 指定所有型別宣告的根命名空間。  這個參數對應於 vbc.exe 編譯器的 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) 參數。|  
|`SdkPath`|選擇性 `String` 參數。<br /><br /> 指定 mscorlib.dll 和 microsoft.visualbasic.dll 的位置。  此參數 \(Parameter\) 對應 vbc.exe 編譯器的 [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) 參數 \(switch\)。|  
|`Sources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一個或多個 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 原始程式檔 \(Source File\)。|  
|`TargetCompactFramework`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，工作便會以 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 為目標。  這個參數對應於 vbc.exe 編譯器的 [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) 參數。|  
|`TargetType`|選擇性 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。  這個參數可以具有 `library` 值 \(建立程式碼程式庫\)、`exe` 值 \(建立主控台應用程式\)、`module` 值 \(建立模組\)，或是 `winexe` 值 \(建立 Windows 程式\)。  預設值為 `library`。  這個參數對應於 vbc.exe 編譯器的 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) 參數。|  
|`Timeout`|選擇性 `Int32` 參數。<br /><br /> 指定以毫秒為單位的時間長度，這段時間過後即結束工作可執行檔。  預設值為 `Int.MaxValue`，表示沒有逾時時間。|  
|`ToolPath`|選擇性 `String` 參數。<br /><br /> 指定工作將會載入基礎可執行檔 \(vbc.exe\) 的位置。  如果未指定此參數，工作會使用對應於執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 之架構版本的 SDK 安裝路徑。|  
|`TreatWarningsAsErrors`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則會將所有警告都視為錯誤。  如需詳細資訊，請參閱 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。|  
|`UseHostCompilerIfAvailable`|選擇性 `Boolean` 參數。<br /><br /> 指示工作使用同處理序 \(In\-Process\) 編譯器物件 \(如果有\)。  僅供 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用。|  
|`Utf8Output`|選擇性 `Boolean` 參數。<br /><br /> 使用 UTF\-8 編碼方式記錄編譯器輸出。  這個參數對應於 vbc.exe 編譯器的 [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) 參數。|  
|`Verbosity`|選擇性 `String` 參數。<br /><br /> 指定編譯器輸出的詳細等級。  詳細等級可以是 `Quiet`、`Normal` \(預設\) 或 `Verbose`。|  
|`WarningsAsErrors`|選擇性 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。  如需詳細資訊，請參閱 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 這個參數會覆寫 `TreatWarningsAsErrors` 參數。|  
|`WarningsNotAsErrors`|選擇性 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。  如需詳細資訊，請參閱 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 只有在 `TreatWarningsAsErrors` 參數設定為 `true` 時，這個參數才會有用。|  
|`Win32Icon`|選擇性 `String` 參數。<br /><br /> 在組件中插入.ico檔，讓輸出檔具有在檔案總管中所需的外觀。  這個參數對應於 vbc.exe 編譯器的 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) 參數。|  
|`Win32Resources`|選擇性 `String` 參數。<br /><br /> 將 Win32 資源 \(.res\) 檔插入輸出檔中。  這個參數對應於 vbc.exe 編譯器的 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) 參數。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)。  
  
## 範例  
 下列程式碼範例會編譯 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案。  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)