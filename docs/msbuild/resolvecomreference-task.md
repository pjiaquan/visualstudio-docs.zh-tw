---
title: "ResolveComReference Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference task"
  - "ResolveCOMReference task [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# ResolveComReference Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得一個或多個型別程式庫名稱或 .tlb 檔的清單，並將那些型別程式庫解析至磁碟上的位置。  
  
## 參數  
 下表說明 `ResolveCOMReference` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`DelaySign`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，便會將公開金鑰 \(Public Key\) 置於組件中。  如果為 `false`，工作便會對組件完整簽章。|  
|`EnvironmentVariables`|選擇性 `String[]` 參數。<br /><br /> 以等號分隔之環境變數組的陣列。  這些變數會傳遞給繁衍 \(Spawn\) 的 tlbimp.exe 和 aximp.exe，以加入至 \(或選擇性覆寫\) 一般環境區塊。|  
|`ExecuteAsTool`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則從適當目標 Framework 跨處理序執行 tlbimp.exe 和 aximp.exe，以產生必要的包裝函式組件。  此參數會啟用多目標。|  
|`IncludeVersionInInteropName`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則會將 Typelib 版本包含在包裝函式名稱中。  預設值為 `false`。|  
|`KeyContainer`|選擇性 `String` 參數。<br /><br /> 指定保留公開\/私密金鑰組的容器。<br /><br /> 金鑰組。|  
|`KeyFile`|選擇性 `String` 參數。<br /><br /> 指定包含公開\/私密金鑰組的項目。<br /><br /> 金鑰組。|  
|`NoClassMembers`|選擇性 `Boolean` 參數。|  
|`ResolvedAssemblyReferences`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定解析的組件參考。|  
|`ResolvedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定磁碟上對應到型別程式庫實體位置的完整檔案，這些型別程式庫是提供做為這個工作的輸出。|  
|`ResolvedModules`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。|  
|`SdkToolsPath`|選擇性 [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 參數。<br /><br /> 如果 `ExecuteAsTool` 為 `true`，則此參數必須設為當做目標之 Framework 版本的 SDK 工具路徑。|  
|`StateFile`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定 COM 元件時間戳記的快取檔案。  如果不存在，則每次執行都會重新產生所有的包裝函式。|  
|`TargetFrameworkVersion`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定專案的目標 Framework 版本。<br /><br /> 預設值為 `String.Empty`。  表示不會根據目標 Framework 篩選參考。|  
|`TargetProcessorArchitecture`|選擇性 assetId:///String?qualifyHint=False&autoUpgrade=True 參數。<br /><br /> 指定慣用的目標處理器架構。  已在轉譯後傳遞至 tlbimp.exe \/machine 旗標。<br /><br /> 參數值必須是 <xref:Microsoft.Build.Utilities.ProcessorArchitecture> 的成員。|  
|`TypeLibFiles`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 COM 參考的型別程式庫檔案路徑。  此參數所包含的項目可能會包含項目中繼資料 \(Metadata\)。  如需詳細資訊，請參閱以下的「TypeLibFiles 項目中繼資料」一節。|  
|`TypeLibNames`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要解析的型別程式庫名稱。  此參數所包含的項目必須包含某些項目中繼資料。  如需詳細資訊，請參閱以下的「TypeLibNames 項目中繼資料」一節。|  
|`WrapperOutputDirectory`|選擇性 `String` 參數。<br /><br /> 所產生之 Interop 組件在磁碟上的位置。  如果未指定這個項目中繼資料，則工作會使用專案檔所在目錄的絕對路徑。|  
  
## 備註  
  
## TypeLibNames 項目中繼資料  
 下表針對傳遞至 `TypeLibNames` 參數的項目，說明項目可用的中繼資料。  
  
|Metadata|描述|  
|--------------|--------|  
|`GUID`|必要的項目中繼資料。<br /><br /> 型別程式庫的 GUID。  如果未指定這個項目中繼資料，則工作會失敗。|  
|`VersionMajor`|必要的項目中繼資料。<br /><br /> 型別程式庫的主要版本。  如果未指定這個項目中繼資料，則工作會失敗。|  
|`VersionMinor`|必要的項目中繼資料。<br /><br /> 型別程式庫的次要版本。  如果未指定這個項目中繼資料，則工作會失敗。|  
|`LocaleIdentifier`|選擇性項目中繼資料。<br /><br /> 型別程式庫的地區設定識別項 \(或稱為 LCID\)。  此項目是指定為 32 位元值，此值可辨識使用者、區域或應用程式慣用的人類語言。  如果未指定這個項目中繼資料，則工作會使用預設的地區設定識別項 "0"。|  
|`WrapperTool`|選擇性項目中繼資料。<br /><br /> 指定包裝函式工具，此工具可用來針對這個型別程式庫產生組件包裝函式。  如果未指定這個項目中繼資料，則工作會使用預設的包裝函式工具 "tlbimp"。  不區分大小寫的可用 typelib 選項如下：<br /><br /> -   `Primary`：如果要針對 COM 元件使用已產生的主要 Interop 組件，請使用這個包裝函式工具。  使用這個包裝函式工具時，請勿指定包裝函式輸出目錄，因為那樣會造成工作失敗。<br />-   `TLBImp`：如果要針對 COM 元件產生 Interop 組件，請使用這個包裝函式工具。<br />-   `AXImp`: 例如，當您想要產生ActiveX控制項產生Interop組件，請使用這個包裝函式工具。|  
  
## TypeLibFiles 項目中繼資料  
 下表針對傳遞至 `TypeLibFiles` 參數的項目，說明項目可用的中繼資料。  
  
|Metadata|描述|  
|--------------|--------|  
|`WrapperTool`|選擇性項目中繼資料。<br /><br /> 指定包裝函式工具，此工具可用來針對這個型別程式庫產生組件包裝函式。  如果未指定這個項目中繼資料，則工作會使用預設的包裝函式工具 "tlbimp"。  不區分大小寫的可用 typelib 選項如下：<br /><br /> -   `Primary`：如果要針對 COM 元件使用已產生的主要 Interop 組件，請使用這個包裝函式工具。  使用這個包裝函式工具時，請勿指定包裝函式輸出目錄，因為那樣會造成工作失敗。<br />-   `TLBImp`：如果要針對 COM 元件產生 Interop 組件，請使用這個包裝函式工具。<br />-   `AXImp`:例如，當您想要產生ActiveX控制項產生Interop組件，請使用這個包裝函式工具。|  
  
> [!NOTE]
>  當您提供越多資訊以唯一識別型別程式庫時，工作就越可能解析至磁碟上的正確檔案。  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Utilities.Task> 類別的參數。  如需這些其他參數的清單及其描述，請參閱 [Task Base Class](../msbuild/task-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)