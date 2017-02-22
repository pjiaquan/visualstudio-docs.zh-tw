---
title: "MT Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT task"
  - "MT task (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MT Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 Microsoft 資訊清單工具 \(mt.exe\)。  如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的「Mt.exe」。  
  
## 參數  
 下表說明 **MT** 工作的參數。  大部分的工作參數及部分參數集會對應到命令列選項。  
  
> [!NOTE]
>  mt.exe 文件使用連字號 \(**\-**\) 做為命令列選項的前置詞，但本主題會使用斜線 \(**\/**\)。  兩個前置詞都是可接受的。  
  
|參數|描述|  
|--------|--------|  
|**AdditionalManifestFiles**|選擇性 **String\[\]** 參數。<br /><br /> 指定一或多個資訊清單的檔案名稱。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/manifest** 選項。|  
|**AdditionalOptions**|選擇性 **String** 參數。<br /><br /> 命令列選項的清單。  例如 "*\/option1 \/option2 \/option\#*"。  使用這個參數來指定不由其他任何 **MT** 工作參數代表的命令列選項。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的「Mt.exe」。|  
|**AssemblyIdentity**|選擇性 **String** 參數。<br /><br /> 指定資訊清單 **assemblyIdentity** 項目的屬性值。  指定以逗號分隔的清單，其中第一個元件是 `name` 屬性的値，後面跟著一或多個名稱\/值組，其形式為 *\<attribute name\>\=\<attribute\_value\>*。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/identity** 選項。|  
|**ComponentFileName**|選擇性 **String** 參數。<br /><br /> 指定您想要利用 .rgs 或 .tlb 檔案建置的動態連結程式庫的名稱。  如果您指定 **RegistrarScriptFile** 或 **TypeLibraryFile** MT 工作參數，就需要這個參數。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/dll** 選項。|  
|**DependencyInformationFile**|選擇性 **String** 參數。<br /><br /> 指定 Visual Studio 用來追蹤資訊清單工具的組建相依性資訊的相依資訊檔。|  
|**EmbedManifest**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，會將資訊清單檔內嵌在組件中。  如果 `false`，會建立為獨立的資訊清單檔案。|  
|**EnableDPIAwareness**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，請加入將應用程式標記為 DPI 感知的資訊清單資訊。  撰寫 DPI 感知應用程式可讓各種不同高 DPI 顯示設定的使用者介面顯得一致。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的「高 DPI」。|  
|**GenerateCatalogFiles**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，會產生目錄定義 \(.cdf\) 檔案。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/makecdfs** 選項。|  
|**GenerateCategoryTags**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，會造成產生分類標籤。  如果這個參數是 `true`，則必須同時指定**ManifestFromManagedAssembly MT** 工作參數。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/category** 選項。|  
|**InputResourceManifests**|選擇性 **String** 參數。<br /><br /> 從具有指定識別項且型別為 RT\_MANIFEST 的資源輸入資訊清單。  指定此形式的資源：*\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*，其中選擇性的 `resource_id` 參數是非負數的 16 位元數字。<br /><br /> 如果不指定任何 `resource_id`，會使用 CREATEPROCESS\_MANIFEST\_RESOURCE 預設值 \(1\)。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/inputresource** 選項。|  
|**ManifestFromManagedAssembly**|選擇性 **String** 參數。<br /><br /> 從指定的 Managed 組件產生資訊清單。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/managedassemblyname** 選項。|  
|**ManifestToIgnore**|選擇性 **String** 參數。<br /><br /> \(未使用\)。|  
|**OutputManifestFile**|選擇性 **String** 參數。<br /><br /> 指定輸出資訊清單。  如果省略此參數，而且只操作一個資訊清單，則會在原地修改該資訊清單。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/out** 選項。|  
|**OutputResourceManifests**|選擇性 **String** 參數。<br /><br /> 將資訊清單輸出到具有指定識別項的型別 RT\_MANIFEST。  資源的形式為 *\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*，其中選擇性的 `resource_id` 參數是非負數的 16 位元數字。<br /><br /> 如果不指定任何 `resource_id`，會使用 CREATEPROCESS\_MANIFEST\_RESOURCE 預設值 \(1\)。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/outputresource** 選項。|  
|**RegistrarScriptFile**|選擇性 **String** 參數。<br /><br /> 指定使用免註冊 COM 資訊清單支援之登錄器指令碼 \(.rgs\) 檔的名稱。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/rgs** 選項。|  
|**ReplacementsFile**|選擇性 **String** 參數。<br /><br /> 指定檔案，此檔案包含登錄器指令碼 \(.rgs\) 檔中可置換字串的値。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/replacements** 選項。|  
|**ResourceOutputFileName**|選擇性 **String** 參數。<br /><br /> 指定用來將資訊清單內嵌到專案輸出的輸出資源檔案。|  
|**Sources**|選擇性 `ITaskItem[]` 參數。<br /><br /> 指定以空格分隔的資訊清單來源檔清單。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/manifest** 選項。|  
|**SuppressDependencyElement**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，會產生不含相依性項目的資訊清單。  如果這個參數是 `true`，亦指定 **ManifestFromManagedAssembly MT** 工作參數。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/nodependency** 選項。|  
|**SuppressStartupBanner**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，可防止在工作啟動時顯示版權和版本號碼訊息。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性 `String` 參數。<br /><br /> 指定用於儲存此工作之追蹤記錄檔的中繼目錄。|  
|**TypeLibraryFile**|選擇性 **String** 參數。<br /><br /> 指定型別程式庫 \(.tlb\) 檔案的名稱。  如果指定這個參數，請同時指定 **ComponentFileName MT** 工作參數。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/tlb** 選項。|  
|**UpdateFileHashes**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，則在 **UpdateFileHashesSearchPath MT**工作參數所指定的路徑計算檔案的雜湊値，然後使用計算出來的値更新資訊清單之 **file** 項目中 **hash** 屬性的値。<br /><br /> 需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上＜Mt.exe＞中的 **\/hashupdate** 選項。  請參閱這個資料表中的 **UpdateFileHashesSearchPath** 參數。|  
|**UpdateFileHashesSearchPath**|選擇性 `String` 參數。<br /><br /> 指定更新檔案雜湊時要使用搜尋路徑。  請搭配這個參數使用 **UpdateFileHashes MT** 工作參數。<br /><br /> 如需詳細資訊，請參閱本表中的 **UpdateFileHashes** 參數。|  
|**VerboseOutput**|選擇性 `Boolean` 參數。<br /><br /> 如果 `true`，會顯示詳細的偵錯資訊。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上「Mt.exe」中的 **\/verbose** 選項。|  
  
## 備註  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)