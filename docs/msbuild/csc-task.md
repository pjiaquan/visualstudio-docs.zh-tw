---
title: "Csc 工作 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc 工作 [MSBuild]"
  - "MSBuild，Csc 工作"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Csc 工作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 CSC.exe，並會產生可執行檔 （.exe 檔）、 動態連結程式庫 （.dll 檔案） 或程式碼模組 （.netmodule 檔）。 如需 CSC.exe 的詳細資訊，請參閱 [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/index)。  
  
## <a name="parameters"></a>參數  
 下表說明 `Csc` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`AdditionalLibPaths`|選擇性的 `String[]` 參數。<br /><br /> 指定要搜尋參考的其他目錄。 如需詳細資訊，請參閱 [/lib （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option)。|  
|`AddModules`|選擇性的 `String` 參數。<br /><br /> 指定要成為組件一部分的一個或多個模組。 如需詳細資訊，請參閱 [/addmodule （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option)。|  
|`AllowUnsafeBlocks`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，使用的程式碼編譯 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 關鍵字。 如需詳細資訊，請參閱 [/unsafe （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)。|  
|`ApplicationConfiguration`|選擇性的 `String` 參數。<br /><br /> 指定包含組件繫結設定的應用程式組態檔。|  
|`BaseAddress`|選擇性的 `String` 參數。<br /><br /> 指定載入 DLL 時慣用的基底位址。 DLL 預設基底位址由設定 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 通用語言執行平台。 如需詳細資訊，請參閱 [/baseaddress （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)。|  
|`CheckForOverflowUnderflow`|選擇性的 `Boolean` 參數。<br /><br /> 指定整數算術在超出範圍的資料型別是否會在執行階段例外狀況。 如需詳細資訊，請參閱 [/checked （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)。|  
|`CodePage`|選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 如需詳細資訊，請參閱 [/codepage （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option)。|  
|`DebugType`|選擇性的 `String` 參數。<br /><br /> 指定偵錯類型。 `DebugType` 可以是 `full` 或 `pdbonly`。 預設值是 `full`, ，可讓偵錯工具附加至執行中的程式。 指定 `pdbonly` 啟用來源程式啟動偵錯工具，但執行的程式附加到偵錯工具時，才會顯示組譯工具時，偵錯程式碼。<br /><br /> 這個參數會覆寫 `EmitDebugInformation` 參數。<br /><br /> 如需詳細資訊，請參閱 [/debug （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。|  
|`DefineConstants`|選擇性的 `String` 參數。<br /><br /> 定義前置處理器符號。 如需詳細資訊，請參閱 [/ 定義 （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)。|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，指定您想要完整簽署組件。 如果 `false`, ，指定您只想要將組件中的公開金鑰。<br /><br /> 此參數沒有任何作用，除非用於 `KeyFile` 或 `KeyContainer` 參數。<br /><br /> 如需詳細資訊，請參閱 [/delaysign （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option)。|  
|`DisabledWarnings`|選擇性的 `String` 參數。<br /><br /> 指定要停用的警告清單。 如需詳細資訊，請參閱 [/nowarn （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)。|  
|`DocumentationFile`|選擇性的 `String` 參數。<br /><br /> 將文件註解處理成 XML 檔案。 如需詳細資訊，請參閱 [/doc （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)。|  
|`EmitDebugInformation`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，工作會產生偵錯資訊，並將它放在程式資料庫 (.pdb) 檔案。 如果 `false`, ，工作會發出任何偵錯資訊。 預設為 `false`。 如需詳細資訊，請參閱 [/debug （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。|  
|`ErrorReport`|選擇性的 `String` 參數。<br /><br /> 提供 C# 內部錯誤回報給 Microsoft 的便利方式。 這個參數可以為 `prompt`, ，`send`, ，或 `none`。 如果此參數設定為 `prompt`, ，編譯器內部錯誤發生時，您會收到提示。 在提示字元可讓您以電子方式將錯誤報告傳送給 Microsoft。 如果此參數設定為 `send`, ，就會自動傳送錯誤報告。 如果此參數設定為 `none`, ，只在編譯器的文字輸出中報告的錯誤。 預設為 `none`。 如需詳細資訊，請參閱 [/errorreport （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)。|  
|`FileAlignment`|選擇性的 `Int32` 參數。<br /><br /> 指定輸出檔案中區段的大小。 如需詳細資訊，請參閱 [/filealign （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)。|  
|`GenerateFullPaths`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，在編譯器輸出中指定檔案的絕對路徑。 如果 `false`, ，指定檔案的名稱。 預設為 `false`。 如需詳細資訊，請參閱 [/fullpaths （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option)。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 如需詳細資訊，請參閱 [/keycontainer （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option)。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 如需詳細資訊，請參閱 [/keyfile （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option)。|  
|`LangVersion`|選擇性的 `String` 參數。<br /><br /> 指定要使用的語言版本。 如需詳細資訊，請參閱 [/langversion （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)。|  
|`LinkResources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 建立的連結 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 輸出檔案中的資源的資源檔不會在輸出檔中。<br /><br /> 傳入此參數的項目可以有選擇性中繼資料的項目名為 `LogicalName` 和 `Access`。 `LogicalName` 對應至 `identifier` 參數 `/linkresource` 切換，以及 `Access` 對應至 `accessibility-modifier` 參數。 如需詳細資訊，請參閱 [/linkresource （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)。|  
|`MainEntryPoint`|選擇性的 `String` 參數。<br /><br /> 指定的位置 `Main` 方法。 如需詳細資訊，請參閱 [/main （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)。|  
|`ModuleAssemblyName`|選擇性的 `String` 參數。<br /><br /> 指定此模組一部分的組件名稱。|  
|`NoConfig`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，告訴編譯器不使用 csc.rsp 檔案進行編譯。 如需詳細資訊，請參閱 [/noconfig （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option)。|  
|`NoLogo`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，隱藏編譯器橫幅資訊。 如需詳細資訊，請參閱 [/nologo （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option)。|  
|`NoStandardLib`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，可防止匯入的 mscorlib.dll，它會定義整個系統命名空間。 如果您想要定義或建立自己的系統命名空間和物件，請使用此參數。 如需詳細資訊，請參閱 [/nostdlib （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)。|  
|`NoWin32Manifest`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，不包含預設的 Win32 資訊清單。|  
|`Optimize`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，啟用最佳化。 如果 `false`, ，會停用最佳化。 如需詳細資訊，請參閱 [/optimize （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)。|  
|`OutputAssembly`|選擇性 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 如需詳細資訊，請參閱 [/out （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)。|  
|`PdbFile`|選擇性的 `String` 參數。<br /><br /> 指定偵錯資訊檔案名稱。 預設名稱是輸出檔案名稱副檔名為.pdb。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 這個參數可以為 `x86`, ，`x64`, ，或 `anycpu`。 預設為 `anycpu`。 如需詳細資訊，請參閱 [/platform （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)。|  
|`References`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 讓指定的項目從公用型別資訊匯入到目前專案的工作。 如需詳細資訊，請參閱 [/reference （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)。<br /><br /> 您可以指定 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 參考別名中 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 檔案中的加入中繼資料 `Aliases` 與原始的 「 參考 」 項目。 例如，若要設定別名"LS1"下列 CSC 命令列︰<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> 您可以使用︰<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將內嵌 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 資源至輸出檔。<br /><br /> 傳入此參數的項目可以有選擇性中繼資料的項目名為 `LogicalName` 和 `Access`。 `LogicalName` 對應至 `identifier` 參數 `/resource` 切換，以及 `Access` 對應至 `accessibility-modifier` 參數。 如需詳細資訊，請參閱 [/resource （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)。|  
|`ResponseFiles`|選擇性的 `String` 參數。<br /><br /> 指定包含這項工作的命令的回應檔案。 如需詳細資訊，請參閱 [@ （指定回應檔）](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option)。|  
|`Sources`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 原始程式檔。|  
|`TargetType`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 這個參數可以具有的值 `library`, ，它會建立程式碼程式庫 `exe`, ，這樣就可以建立主控台應用程式， `module`, ，這樣就可以建立一個模組，或 `winexe`, ，它會建立 Windows 程式。 預設值是 `library`。 如需詳細資訊，請參閱 [/target （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)。|  
|`TreatWarningsAsErrors`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`, ，將所有警告視為錯誤。 如需詳細資訊，請參閱 [/warnaserror （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。|  
|`UseHostCompilerIfAvailable`|選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，會指示工作使用同處理序編譯器物件。 僅供 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|`Utf8Output`|選擇性的 `Boolean` 參數。<br /><br /> 記錄編譯器輸出使用 utf-8 編碼方式。 如需詳細資訊，請參閱 [/utf8output （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option)。|  
|`WarningLevel`|選擇性的 `Int32` 參數。<br /><br /> 指定要顯示編譯器警告層級。 如需詳細資訊，請參閱 [/warn （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)。|  
|`WarningsAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。<br /><br /> 這個參數會覆寫 `TreatWarningsAsErrors` 參數。|  
|`WarningsNotAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。<br /><br /> 這個參數才有用如果 `TreatWarningsAsErrors` 參數設為 `true`。|  
|`Win32Icon`|選擇性的 `String` 參數。<br /><br /> 將.ico 檔案插入組件，讓輸出檔在檔案總管中所要的外觀。 如需詳細資訊，請參閱 [/win32icon （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)。|  
|`Win32Manifest`|選擇性的 `String` 參數。<br /><br /> 指定要包含 Win32 資訊清單。|  
|`Win32Resource`|選擇性的 `String` 參數。<br /><br /> 將 Win32 資源 (.res) 檔插入至輸出檔。 如需詳細資訊，請參閱 [/win32res （C# 編譯器選項）](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option)。|  
  
## <a name="remarks"></a>備註  
 除了上面所列的參數，此工作會繼承來自參數 `Microsoft.Build.Tasks.ManagedCompiler` 類別繼承自 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 本身的類別繼承自 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 這些額外的參數及其描述的清單，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Csc` 來編譯原始程式檔中的可執行檔的工作 `Compile` 項目集合。  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)