---
title: "如何：清除組建 | Microsoft Docs"
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
  - "目錄 [.NET Framework], 輸出項目"
  - "Exec 工作 [MSBuild]"
  - "MSBuild, 清除建置"
  - "輸出, 移除項目"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：清除組建
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

清除組建 \(Build\) 時，所有的中繼檔和輸出檔都會刪除，只留下專案檔和元件檔。  接著再從專案檔和元件檔中，建置 \(Build\) 中繼檔和輸出檔的新執行個體。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 隨附的一般工作程式庫中包含 [Exec](../msbuild/exec-task.md) 工作，您可以用此工作來執行系統命令。  如需工作程式庫的詳細資訊，請參閱 [Task Reference](../msbuild/msbuild-task-reference.md)。  
  
## 建立輸出項目的目錄  
 在您編譯專案時所建立的 .exe 檔，其預設位置是在與專案檔和原始程式檔 \(Source File\) 相同的目錄。  不過，輸出項目通常會建立在另一個目錄中。  
  
#### 若要建立輸出項目的目錄  
  
1.  使用 `Property` 項目來定義目錄的位置和名稱。  例如，在包含專案檔和原始程式檔的目錄中，建立名為 `BuiltApp` 的目錄：  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  如果這個目錄不存在，請使用 [MakeDir](../msbuild/makedir-task.md) 工作加以建立。  例如：  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## 移除輸出項目  
 在建立中繼檔和輸出檔的新執行個體前，您可能想先清除中繼檔和輸出檔先前的所有執行個體。  請使用 [RemoveDir](../msbuild/removedir-task.md) 工作，從磁碟中刪除目錄以及其中包含的所有檔案和目錄。  
  
#### 若要刪除目錄和其中所包含的所有檔案  
  
-   使用 `RemoveDir` 工作來移除目錄。  例如：  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## 範例  
 下列程式碼範例的專案中含有新目標 \(Target\) `Clean`，此目標使用 `RemoveDir` 工作刪除目錄和其中包含的所有檔案和目錄。  同樣在這個範例中，`Compile` 目標會建立另一個目錄供輸出項目使用，這些輸出項目會在組建清除之後刪除。  
  
 `Compile` 被定義為預設目標，因此會自動使用，除非您指定其他目標。  您可以使用命令列參數 **\/target** 來指定不同的目標。  例如：  
  
 `msbuild <file name>.proj /target:Clean`  
  
 **\/target** 參數可以縮寫為 **\/t**，並且能指定一個以上的目標。  例如，若要依序使用 `Clean` 和 `Compile` 目標，請輸入：  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [Exec Task](../msbuild/exec-task.md)   
 [MakeDir Task](../msbuild/makedir-task.md)   
 [RemoveDir Task](../msbuild/removedir-task.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [目標](../msbuild/msbuild-targets.md)