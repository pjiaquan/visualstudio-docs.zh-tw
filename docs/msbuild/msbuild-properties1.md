---
title: "MSBuild Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild 屬性"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Properties1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

屬性是可用來設定組建的名稱 / 值組。 屬性可用於將值傳遞給工作、 評估條件，以及儲存將整個專案檔中參考的值。  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>定義和參考專案檔中的屬性  
 藉由建立具有屬性的名稱為子系的項目宣告屬性的 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 項目。 例如，下列 XML 程式碼會建立名為的屬性 `BuildDir` ，其值的 `Build`。  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 整個專案檔，會在參考屬性使用語法 $(`PropertyName`)。 例如，在上述範例中的屬性參考使用 $(BuildDir)。  
  
 重新定義屬性，可以變更屬性值。  `BuildDir` 屬性可以使用此 XML 指定新值︰  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 屬性會以其出現在專案檔中的順序進行評估。 新值 `BuildDir` 舊的值指派給之後必須宣告。  
  
## <a name="reserved-properties"></a>保留的屬性  
 MSBuild 保留一些屬性名稱來儲存專案檔和 MSBuild 二進位檔案的相關資訊。 這些屬性會參考使用 $ 標記法，如同任何其他內容。 例如，$(MSBuildProjectFile) 傳回專案檔，包括檔案名稱副檔名的完整檔案的名稱。  
  
 如需詳細資訊，請參閱 [如何︰ 參考的名稱或專案檔的位置](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) 和 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。  
  
## <a name="environment-properties"></a>環境屬性  
 就像參考保留的屬性，您可以參考專案檔中的環境變數。 例如，若要使用 `PATH` 環境變數，在專案檔中，使用 $（路徑）。 如果專案包含具有相同名稱的環境屬性的屬性定義，在專案屬性會覆寫環境變數的值。  
  
 每個 MSBuild 專案都有獨立的環境區塊：只會看見本身區塊中讀取和寫入的內容。  在評估或建立專案檔案之前，MSBuild 只會在初始化屬性集合時讀取環境變數。 在此之後，環境屬性會是靜態的，也就是說，每個繁衍的工具一開始都會採用相同的名稱和值。  
  
 若要取得目前從繁衍的工具內的環境變數的值，請使用 [屬性函式](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable。 慣用的方法，不過，是使用工作參數 <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>。 這個字串陣列中設定的環境屬性可以傳遞至繁衍的工具，而不會影響系統環境變數。  
  
> [!TIP]
>  並非所有環境變數都會在讀取後變成初始屬性。 任何未採用有效 MSBuild 屬性名稱 (例如 "386") 的環境變數都會被忽略。  
  
 如需詳細資訊，請參閱 [How to︰ 在組建中使用環境變數](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)。  
  
## <a name="registry-properties"></a>登錄內容  
 可使用下列語法，來讀取系統登錄值其中 `Hive` 是登錄 hive (例如 HKEY_LOCAL_MACHINE) `Key` 是索引鍵的名稱， `SubKey` 子機碼名稱，以及 `Value` 子機碼值。  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 若要取得預設子機碼值，請省略 `Value`。  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 此登錄值可以用來初始化建置屬性中。 例如，若要建立一個組建屬性，表示 Visual Studio web 瀏覽器首頁，使用此程式碼︰  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>全域屬性  
 MSBuild 可讓您使用命令列上設定屬性 **/property** (或 **/p**) 切換。 這些全域屬性值會覆寫專案檔中所設定的屬性值。 這包括環境屬性，但不包含保留的屬性，就無法變更。  
  
 下列範例會將全域 `Configuration` 屬性 `DEBUG`。  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 也可設定或修改的子專案在多專案的組建中使用全域屬性 `Properties` MSBuild 工作的屬性。 如需詳細資訊，請參閱 [MSBuild 工作](../msbuild/msbuild-task.md)。  
  
 如果您使用專案標記中的 `TreatAsLocalProperty` 屬性 (Attribute) 指定屬性 (Property)，該全域屬性 (Property) 值就不會覆寫專案檔中設定的屬性 (Property) 值。 如需詳細資訊，請參閱 [專案項目 (MSBuild)](../msbuild/project-element-msbuild.md) 和 [How to︰ 建置使用不同的選項相同原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)。  
  
## <a name="property-functions"></a>屬性函式  
 從 .NET Framework 4 版開始，您可以使用屬性函式評估您的 MSBuild 指令碼。 您可以讀取系統時間、 比較字串、 比對規則運算式，並對建置指令碼中執行許多其他動作，而不使用 MSBuild 工作。  
  
 您可以使用字串 （執行個體） 方法操作任何屬性值，以及您可以呼叫許多系統類別的靜態方法。 例如，您可以設定建置屬性設為今天的日期，如下所示。  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 如需詳細資訊，屬性函式的清單，請參閱 [屬性函式](../msbuild/property-functions.md)。  
  
## <a name="creating-properties-during-execution"></a>在執行期間建立的屬性  
 內容位置外 `Target` 項目會指派值給組建的評估階段。 在後續的執行階段，屬性可以建立或修改，如下所示︰  
  
-   屬性可以發出任何工作。 若要發出屬性， [工作](../msbuild/task-element-msbuild.md) 項目必須有一個子系 [輸出](../msbuild/output-element-msbuild.md) 項目具有 `PropertyName` 屬性。  
  
-   屬性可以發出 [CreateProperty](../msbuild/createproperty-task.md) 工作。 這種使用方式已被取代。  
  
-   在.NET Framework 3.5 中，啟動 `Target` 項目可能包含 `PropertyGroup` 可能會包含屬性宣告的項目。  
  
## <a name="storing-xml-in-properties"></a>將 XML 儲存在屬性  
 屬性可以包含任意 XML，將值傳遞給工作，或是顯示記錄資訊可幫助。 下列範例所示 `ConfigTemplate` 屬性，其中包含 XML 和其他屬性的值的參考。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 藉由其各自的屬性值取代屬性參考。 屬性值會指派以它們出現的順序。 因此，在此範例中， `$(MySupportedVersion)`, ，`$(MyRequiredVersion)`, ，和 `$(MySafeMode)` 應該已定義。  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [如何︰ 在組建中使用環境變數](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [如何︰ 參考的名稱或專案檔的位置](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [如何︰ 建置使用不同的選項相同原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [屬性項目 (MSBuild)](../msbuild/property-element-msbuild.md)