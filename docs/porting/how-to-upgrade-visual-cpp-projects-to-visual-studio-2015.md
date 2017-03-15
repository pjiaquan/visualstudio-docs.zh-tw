---
title: "如何：將 Visual C++ 專案升級為 Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [C++]，升級"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將 Visual C++ 專案升級為 Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

第一次開啟使用舊版 Visual Studio 建立的 Visual C\+\+ 專案時，系統可能會提示您更新專案。 訊息詢問您是否要升級到 Visual C\+\+ 編譯器和程式庫的最新版本。 升級選項取決於用於建立專案的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本。  
  
 您可以使用 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 開啟、編輯和建置在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中建立的 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 專案，但若要建立新的 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 專案，您必須使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] \(若要建立 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 專案，您必須使用 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]\)。  
  
 若要建立 Windows 10 專案，您必須使用 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]。  
  
 如果沒有提示您更新專案，您可能不需要執行任何動作來升級專案。 如需詳細資訊，請參閱 [移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)。  
  
-   如果專案 \(.vcproj\) 是在比 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 還要舊的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本中建立的，您必須更新專案。  
  
-   如果專案 \(.vcxproj\) 是在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 或 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中建立的，您有兩個選擇：  
  
    -   您可以略過更新。[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 會載入專案而不進行任何變更 \(如果可以在含 SP1 的 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 或 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中存取 Visual C\+\+ 工具\)。 您可以在具有 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 的相同電腦上安裝建立專案所使用的 Visual Studio 版本，以提供這項存取權。 如需詳細資訊，請參閱[並存安裝 Visual Studio 版本](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)。  
  
    -   若要更新專案，您可允許 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 進行本主題稍後說明的變更。 如果您的方案有一個以上的 Visual C\+\+ 專案，則必須全部更新。  
  
        > [!NOTE]
        >  如果您在第一次提示時拒絕更新，稍後可以選取 \[專案\] 功能表上的 \[更新 VC\+\+ 專案\] 更新專案。 如果命令未出現，則不需要更新。  
  
## 升級 Visual C\+\+ 專案  
 如果您允許 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 自動更新專案，則會進行下列變更：  
  
-   變更專案，讓它使用 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 編譯器和程式庫 \(PlatformToolset \= VisualStudio v140\)。  
  
-   若是 [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] 專案，則會將 TargetFrameworkVersion 變更為 .NET Framework 4.5.2。  
  
## 繼續使用自訂 PlatformToolset  
 如果您想要繼續使用 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] 中的自訂 PlatformToolset，此工具組必須位於 x86 電腦的 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ 底下，或者位於 x64 電腦的 %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ 底下。 如需如何建立自訂 PlatformToolset 的詳細資訊，請參閱 Visual C\+\+ 團隊部落格中的 [C\+\+ 原生多目標](http://go.microsoft.com/fwlink/?LinkId=248587)。  
  
## 請參閱  
 [移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)