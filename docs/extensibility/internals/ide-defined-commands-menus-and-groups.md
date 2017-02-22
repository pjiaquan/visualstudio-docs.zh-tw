---
title: "IDE 定義的命令、 功能表和群組 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "環境定義的命令"
  - ".vsct 檔案，環境定義常數"
  - "環境定義的命令群組"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 定義的命令、 功能表和群組
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

許多的功能表、 命令和命令群組已經定義以供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 當您擴充時，還有可供您使用這些命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 找出環境定義的命令  
 中的一組四個.vsct 檔案會定義環境命令︰  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 這些檔案都位於 *\< Visual Studio SDK 安裝路徑 \>*\\VisualStudioIntegration\\Common\\Inc\\。 這些檔案提供定義和功能表和群組，您可以使用 VSPackage 命令資料表 \(.vsct\) 組態檔中做為容器您自己的功能表、 群組和命令的 Guid。  
  
## 本章節內容  
 [Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 會提供在 Visual Studio 功能表列上的功能表和它們所包含的群組 GUID 和 ID 值。  
  
 [Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 提供 Visual Studio IDE 中的工具列和它們所包含的群組的 GUID 和 ID 值。  
  
 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 提供的 GUID 和 ID 值的 Visual Studio IDE 所定義的命令。  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE 定義的命令，來擴充專案系統](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)