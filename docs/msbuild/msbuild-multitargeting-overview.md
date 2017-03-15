---
title: "MSBuild 多目標概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# MSBuild 多目標概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 MSBuild，您可以將應用程式編譯為可在任何一個 .NET Framework 版本與任何一個系統平台上運行。  例如，您可以將應用程式編譯為在 .NET Framework 2.0 的 32\-bit 版上執行，並將同一個應用程式編譯為在 .NET Framework 4 的 64\-bit 版上執行。  
  
> [!IMPORTANT]
>  儘管名稱為「多目標」，專案只能一次以一種 framework 和一個平台為目標。  
  
 這些是 MSBuild 的目標功能:  
  
-   您可以開發以較舊版 .NET Framework \(例如 2.0、3.5 或 4 版\) 為目標的應用程式。  
  
-   您可以以 .NET Framework 以外的 Framework 為目標，例如 Silverlight Framework。  
  
-   您可以以「*架構設定檔*」\(Framework Profile\) 為目標，這是預先定義的目標 Framework 子集。  
  
-   如果 .NET Framework 有 Service Pack 已發行，您可以以它們為目標。  
  
-   MSBuild 目標可保證應用程式只使用目標 Framework 與平台中提供的功能。  
  
## 目標 Framework 和平台。  
 *目標 Framework* 是專案建置後執行的 .NET Framework 版本，而 *目標平台* 是專案建置後執行的執行的平台。例如，您可能想要以在32 位元平台的 .NET Framework 2.0 能執行應用程式為目標，而此平台與 802x86 處理器系列 \(x86\) 相容。  目標 Framework 和目標平台的組合稱為 *目標內容*。  如需詳細資訊，請參閱[目標 Framework 和目標平台](../msbuild/msbuild-target-framework-and-target-platform.md)。  
  
## Toolset \(ToolsVersion\)  
 工具組收集用來建立應用程式的工具、工作和目標。  Toolset 包含編譯器 \(例如 csc.exe 和 vbc.exe\)、通用目標檔 \(microsoft.common.targets\) 以及通用工作檔 \(microsoft.common.tasks\)。  4.5 工具組可用來以 .NET Framework 2.0， 3.0， 3.5， 4 和 4.5 為對象。然而， MSBuild 2.0 Toolset 僅可用於 .NET Framework 2.0 。  如需詳細資訊，請參閱[Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)。  
  
## 參考組件  
 Toolset 中指定的參考組件幫助您設計和建立應用程式。  這些參考組件不只啟用特定目標建置，而且只開放 Visual Studio IDE 中與目標相容的元件和功能。  如需詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。  
  
## 設定目標和工作  
 您可以設定 MSBuild 目標和工作以跨處理序執行，讓您能用您現在執行的版本構建不同版本的內容。例如，在開發電腦上執行 64 位元的 .NET Framework 4.5 時，您能以 32 位元 .NET Framework 2.0 應用程式為建立目標。如需詳細資訊，請參閱[設定目標和工作](../msbuild/configuring-targets-and-tasks.md)。  
  
## 疑難排解  
 如果您嘗試參考不是目標內容的組件，您可能會遇到錯誤。  如需這些錯誤的詳細資訊和得知如何解決，請參閱 [疑難排解 .NET Framework 目標錯誤](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。