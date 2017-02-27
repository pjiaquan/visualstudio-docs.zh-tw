---
title: "擴充的功能表和命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "一般工作的功能表"
  - "VSPackages，功能表工作"
  - ".vsct 檔案] 功能表上的工作"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# 擴充的功能表和命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

命令會將動作和處理程序加入至 Visual Studio 的方式。 在大部分情況下命令會顯示在功能表或工具列。 VSPackage 專案範本會示範如何實作非常基本的命令。 比較麻煩，但仍然有基本的實作，請參閱 [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
 如需 Visual Studio 命令、 功能表和工具列的詳細資訊，請參閱 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 VSPackage 專案的一部分.vsct 檔中定義的命令、 功能表和工具列。 您可以找到 Visual Studio IDE 和.vsct 檔中的資訊 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 下列主題說明如何加入不同類型的命令、 功能表和工具列。  
  
## 在本節中  
 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 說明如何將內容功能表新增至 Visual Studio 功能表列。  
  
 [功能表項目繫結的鍵盤快速鍵](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 說明如何將鍵盤快速鍵 \(例如 CTRL \+ 3\) 加入至功能表項目。  
  
 [將子功能表新增至功能表](../extensibility/adding-a-submenu-to-a-menu.md)  
 說明如何將最上層功能表中子功能表。  
  
 [最近加入的大部分使用子功能表的清單](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 說明如何新增最近使用的清單。  
  
 [建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)  
 描述如何群組，以便它們可以包含多個功能表上的命令項目。  
  
 [將圖示加入至功能表命令](../extensibility/adding-icons-to-menu-commands.md)  
 描述如何將圖示加入至工具列和功能表上的命令。  
  
 [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)  
 說明如何使用 `TextChanges` 旗標來啟用功能表項目動態變更。  
  
 [變更外觀的命令](../extensibility/changing-the-appearance-of-a-command.md)  
 描述如何以動態方式啟用或停用的命令。  
  
 [更新使用者介面](../extensibility/updating-the-user-interface.md)  
 描述如何強制更新使用者介面，以反映最近的變更。  
  
 [當地語系化的功能表命令](../extensibility/localizing-menu-commands.md)  
 說明如何將功能表命令。  
  
## 相關章節