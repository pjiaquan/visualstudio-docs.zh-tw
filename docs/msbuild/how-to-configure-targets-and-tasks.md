---
title: "如何：設定目標和工作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：設定目標和工作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

選取的 MSBuild 工作，可以將這些目標，無論開發電腦環境的環境中執行。  比方說，當您使用 64 位元電腦建置該目標是 32 位元架構的應用程式時，選定的任務所執行的 32 位元處理序中。  
  
> [!NOTE]
>  若是建置工作所撰寫。NET 語言，例如視覺 C\# 或 Visual Basic，並不會無法使用原生資源或工具，那麼它會在執行任何的目標內容，而不需配接。  
  
## UsingTask 屬性和工作參數  
 下列`UsingTask`屬性會影響特定的建置程序中某一任務的所有作業：  
  
-   `Runtime`屬性，如果有的話，設定通用語言執行階段 \(CLR\) 版本，而且可能會花其中一個這些值： `CLR2`， `CLR4`， `CurrentRuntime`，或`*` \(任何執行階段\)。  
  
-   `Architecture`屬性，如果有的話，設定的平台和位元，而且可能會花任何其中一個值： `x86`， `x64`， `CurrentArchitecture`，或`*` \(任何架構\)。  
  
-   `TaskFactory`屬性，如果有的話，請設定任務工廠會建立和執行工作的執行個體，且會使用的值`TaskHostFactory`。  如需詳細資訊，請參閱本文件稍後的工作工廠 」 一節。  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 您也可以使用`MSBuildRuntime`和`MSBuildArchitecture`參數來設定個別任務的目標內容。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 MSBuild 執行工作之前，它會尋找相符的`UsingTask` ，具有相同的目標內容。  參數中指定`UsingTask` ，但不是會在對應的工作會被視為要比對。  指定在 \[工作而不是相對應參數`UsingTask`也會被視為要比對。  如果在未指定參數值，則`UsingTask`或工作，這些值預設為`*` \(任何參數\)。  
  
> [!WARNING]
>  如果多個`UsingTask`存在都符合`TaskName`， `Runtime`，和`Architecture`屬性，才會被評估的最後一個會取代其他人。  
  
 如果在任務上設定參數，MSBuild 會嘗試尋找`UsingTask` ，符合這些參數或者，至少不是與它們相衝突。  多個`UsingTask`可以指定目標的內容相同的工作。  比方說，對不同的目標環境的不同可執行檔的任務大概就像這樣：  
  
```  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## 工作工廠  
 它會執行一項工作之前，MSBuild 會檢查是否會將它指定目前的軟體內容中執行。  如果所以指定的工作，MSBuild 傳送到的 AssemblyTaskFactory，以目前的處理序。 否則，MSBuild 會在任務傳遞的 TaskHostFactory，比對目標環境的程序中執行工作。  即使目前的內容和目標內容相符，您可以強制執行的工作逾時\-跨處理序 \(如隔離、 安全性或其他原因\) 藉由設定`TaskFactory`到`TaskHostFactory`。  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## 虛設的工作參數  
 像任何其他工作的參數， `MSBuildRuntime`和`MSBuildArchitecture`可以從組建屬性設定。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 不像其他工作的參數， `MSBuildRuntime`和`MSBuildArchitecture`並不明顯工作本身。  若要撰寫的工作，並知道其執行所在的內容，您必須測試內容藉由呼叫。NET framework 的好處，或使用組建屬性傳遞到其他的工作參數的內容資訊。  
  
> [!NOTE]
>  `UsingTask`屬性可以設定從工具組和環境屬性。  
  
 `MSBuildRuntime`和`MSBuildArchitecture`參數提供最具彈性的方式，來設定目標內容中，但也最有限的範圍。  一方面，因為它們在工作執行個體本身上設定，而且在即將執行的工作才會評估，他們可以衍生它們從屬性可以在評估階段，並在建置階段的完整範圍的值。  相反地，這些參數只會套用到特定的目標中某一任務的特定執行個體。  
  
> [!NOTE]
>  父節點的內容中，而不儲存在工作主機的內容，會評估工作參數。執行階段或架構層相關 \(例如程式檔案位置\) 的環境變數會評估為符合父節點的值。  不過，如果直接由工作讀取相同的環境變數時，它會正確地評估工作主機的內容中。  
  
## 請參閱  
 [設定目標和工作](../msbuild/configuring-targets-and-tasks.md)