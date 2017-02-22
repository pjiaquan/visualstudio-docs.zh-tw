---
title: "覆寫 ToolsVersion 設定 | Microsoft Docs"
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
  - "MSBuild, 建置方案"
  - "MSBuild, 覆寫 ToolsVersion 設定"
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 覆寫 ToolsVersion 設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以透過三種方法的其中一種，變更專案和方案的工具組：  
  
1.  建置專案時使用 `/ToolsVersion` 參數 \(或簡稱 `/tv`\) 或從命令行使用方案  
  
2.  藉由設定 MSBuild 工作上的 `ToolsVersion` 參數  
  
3.  設定方案中專案的 `$(ProjectToolsVersion)` 屬性。  這可讓您在方案中建置工具組版本與其他專案不同的專案。  
  
## 在命令列組建覆寫專案和方案的 ToolsVersion 設定  
 雖然 Visual Studio 專案通常會使用專案檔中所指定的 ToolsVersion 建置，但您可以在命令列上使用 `/ToolsVersion`  \(或 `/tv`\) 參數複寫該值，使用不同的工具組建置所有專案以及專案對專案間的相依性。  例如：  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 在這個範例中，所有專案都使用 ToolsVersion 12.0 建置 \(但請參閱本主題稍後的＜優先順序＞一節\)。  
  
 在命令列上使用 `/tv` 參數時，您可以選擇在個別專案中使用 `$(ProjectToolsVersion)` 屬性，以使用不同於方案中其他專案的 ToolsVersion 值來進行建置。  
  
## 使用 MSBuild 工作的 ToolsVersion 參數覆寫 ToolsVersion 設定  
 MSBuild 工作是讓專案建置另一個專案的主要方式。  為了讓 MSBuild 工作使用不同於專案中所指定的 ToolsVersion 來建置專案，此參數有一個名為 `ToolsVersion` 的選擇性工作參數。  下列範例示範如何使用這個參數：  
  
1.  建立名為 `projectA.proj` 且包含下列程式碼的檔案：  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  建立另一個名為 `projectB.proj` 且包含下列程式碼的檔案：  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  在命令提示字元中輸入下列命令：  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  下列輸出隨即出現。  對於 `projectA`，命令列上的 `/toolsversion:3.5` 設定會覆寫 `Project` 標記中的 `ToolsVersion=12.0` 設定。  
  
     `ProjectB` 是由 `projectA` 中的工作呼叫。  該工作有 `ToolsVersion=2.0`，這會覆寫 `projectB` 的其他 `ToolsVersion` 設定。  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## 優先順序  
 用來判斷 `ToolsVersion` 的優先順序 \(從最高到最低\)：  
  
1.  用來建置專案的 MSBuild 工作上的 `ToolsVersion` 屬性 \(如果有的話\)。  
  
2.  msbuild.exe 命令中使用的 `/toolsversion` \(或 `/tv`\) 參數 \(如果有的話\)。  
  
3.  如果已設定環境變數 `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`，則使用目前的 `ToolsVersion`。  
  
4.  如果已設定環境變數 `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT`，且專案檔中定義的 `ToolsVersion` 大於目前的 `ToolsVersion`，則使用目前的 `ToolsVersion`。  
  
5.  如果已設定環境變數 `MSBUILDLEGACYDEFAULTTOOLSVERSION`，或未設定 `ToolsVersion`，則使用下列步驟：  
  
    1.  專案檔中 [Project](../msbuild/project-element-msbuild.md) 項目的 `ToolsVersion` 屬性。  如果這個屬性不存在，則會假設為目前的版本。  
  
    2.  MSBuild.exe.config 檔中的預設工具版本。  
  
    3.  登錄中的預設工具版本。  如需詳細資訊，請參閱[標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)。  
  
6.  如果未設定環境變數 `MSBUILDLEGACYDEFAULTTOOLSVERSION`，則使用下列步驟：  
  
    1.  如果環境變數 `MSBUILDDEFAULTTOOLSVERSION` 設為存在的 `ToolsVersion`，則使用它。  
  
    2.  如果在 MSBuild.exe.config 中設定 `DefaultOverrideToolsVersion`，請使用它。  
  
    3.  如果已在登錄中設定 `DefaultOverrideToolsVersion`，則使用它。  
  
    4.  否則請使用目前的 `ToolsVersion`。  
  
## 請參閱  
 [多目標](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)