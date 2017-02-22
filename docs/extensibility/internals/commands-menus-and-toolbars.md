---
title: "命令、 功能表和工具列 | Microsoft Docs"
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
  - "功能表 [Visual Studio SDK] 命令"
  - "命令 [Visual Studio]"
  - "工具列 [Visual Studio] 命令"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
caps.handback.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令、 功能表和工具列
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

功能表和工具列為使用者的方式存取 VSPackage 的命令。 命令是完成工作，例如列印文件、 重新整理檢視，或建立新檔案的功能。 功能表和工具列是方便的圖形化方式，向使用者呈現您的命令。 通常，相同的功能表或工具列上時一起叢集相關的命令。  
  
-   功能表通常顯示為叢集的整合式的開發環境 \(IDE\) 或工具視窗上方的資料列中的一字字串。 功能表也可以顯示為以滑鼠右鍵按一下事件的結果，而且會參照為該內容中的快顯功能表。 按一下時，功能表會展開以顯示一或多個命令。 命令中，按一下時，可以執行工作，或啟動包含其他命令的子功能表。 一些知名的功能表名稱是檔案、 編輯、 檢視和視窗。 如需詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
-   工具列通常是資料列的按鈕和其他控制項，例如下拉式方塊、 清單方塊、 文字方塊和功能表控制器。 工具列上的控制項與相關聯的命令。 當您按一下工具列按鈕時，就會啟動其相關聯的命令。 工具列按鈕通常會有建議的基礎命令，例如印表機的列印命令的圖示。 在下拉式清單控制項中，在清單中的每個項目是與不同的命令產生關聯。 功能表控制器是控制項的在其中一方是控制項的工具列按鈕和的另一面是控制項的向下箭頭，以顯示其他命令時按下的混合。 如需詳細資訊，請參閱[加入至工具列功能表控制器](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)。  
  
-   當您建立的命令時，您也必須建立事件處理常式，它。 事件處理常式會判斷命令何時可見的或啟用，可讓您修改它的文字，並確保會適當地回應命令 \(「 路由 」\) 啟動。 在大部分情況下，IDE 會處理命令使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 中的命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 以階層方式，從最內層的命令內容，而本機範圍，並繼續最外層的內容，而全域範圍開始的路由。 新增至主功能表命令會立即可供指令碼。 如需詳細資訊，請參閱[MenuCommand 對比 OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)與[選擇內容物件](../../extensibility/internals/selection-context-objects.md)。  
  
 若要定義新的功能表和工具列，您必須將這些描述 Visual Studio 命令資料表 \(.vsct\) 檔案中。 在 Visual Studio 封裝範本會建立此檔案，以及必要的項目，以支援任何命令、 工具列和您在範本中選取的編輯器。 或者，您可以撰寫您自己的.vsct 檔，使用此處所描述的 xml 結構描述: [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 如需使用.vsct 檔的詳細資訊，請參閱 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 本章節的主題說明命令、 功能表和工具列如何在 Vspackage 中運作。  
  
## 在本節中  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 命令資料表格式規格的深入說明。  
  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 描述 XML 為基礎的語法和編譯器的命令資料表。  
  
 [預設的命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 描述預先定義的命令、 群組、 功能表和工具列。  
  
 [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 指定預先定義的功能表、 命令和可供使用的命令群組 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 [命令設計](../../extensibility/internals/command-design.md)  
 說明如何設計的命令。  
  
 [最佳化功能表和工具列命令](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 命令會提供指導方針。  
  
 [提供可用的命令](../../extensibility/internals/making-commands-available.md)  
 說明如何讓 Visual Studio 中使用的命令。  
  
 [命令和使用 Interop 組件的功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 說明如何實作使用 interop 組件的命令。  
  
## 相關章節  
 [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)  
 說明 VSPackages 的命令路由。