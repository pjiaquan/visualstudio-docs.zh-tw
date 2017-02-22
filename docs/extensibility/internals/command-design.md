---
title: "命令設計 | Microsoft Docs"
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
  - "命令"
  - "命令中實作"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令設計
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您新增命令到 VSPackage 時，您必須指定就會出現它有的話，以進行處理的是。  
  
## 定義命令  
 若要定義新的命令，請在 VSPackage 專案中加入 Visual Studio 命令表裡 \(.vsct\) 檔案。  如果您使用 Visual Studio 的封裝範本來建立 VSPackage，該專案會包含這些檔案。  如需詳細資訊，請參閱 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 Visual Studio 會合併所有.vsct 找到的檔案後，讓它可以顯示的命令。  因為這些檔案是不同於二進位 VSPackage，Visual Studio 並沒有載入的封裝，若要尋找的命令。  如需詳細資訊，請參閱 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 使用 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>註冊屬性來定義功能表資源和命令。  如需詳細資訊，請參閱 [實作](../../extensibility/internals/command-implementation.md)。  
  
 命令可以在執行階段變更，以多種不同的方式。  它們可以顯示或隱藏、 啟用或停用。  它們可以顯示不同的文字或圖示，或包含不同的值。  Visual Studio 載入您的 VSPackage 之前，可能會執行極大的自訂。  如需詳細資訊，請參閱 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
## 命令處理常式  
 當您建立一個指令時，您必須提供事件處理常式來執行命令。  如果使用者選取命令時，它必須適當地傳送。  路由命令時，表示傳送到正確的 VSPackage 来啟用或停用它，請隱藏或顯示，如果使用者選擇要執行這項操作，請執行它。  如需詳細資訊，請參閱 [路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## 「 Visual Studio 」 命令環境  
 Visual Studio 可裝載任何數目的 VSPackages，而每一個可以提供自己的命令集。  環境即會顯示適用於目前的工作的命令。  如需詳細資訊，請參閱 [可用性](../../extensibility/internals/command-availability.md)和 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)。  
  
 定義新的命令、 功能表、 工具列或快顯功能表的 VSPackage 提供其命令資訊給 Visual Studio 在安裝期間，透過參考在原生或 managed 組件中的資源的登錄項目。  每項資源，然後參考二進位資料 \(.cto\) 的資源檔，當您編譯一個 Visual Studio 命令表裡 \(.vsct\) 檔案時產生。  如此一來提供合併的指令集、 功能表和工具列，而不需要載入每個已安裝的 VSPackage 的 Visual Studio。  
  
### 命令的組織  
 環境將定位群組、 優先順序及功能表的指令。  
  
-   群組為邏輯集合相關的指令，例如， **剪下**， **複製**，以及 **貼上**命令群組。  群組是出現在功能表的指令。  
  
-   優先順序會決定在群組中的個別命令在功能表的顯示的順序。  
  
-   功能表做為容器的群組。  
  
 某些命令、 群組及功能表，預先定義了環境。  如需詳細資訊，請參閱 [預設的命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。  
  
 命令可以指派給主要的群組。  主要群組控制在主功能表結構，然後在指令的位置**自訂**對話方塊。  命令可以出現在多個群組。 例如，命令可以在主功能表、 快顯功能表和工具列上。  如需詳細資訊，請參閱 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
### 命令傳送  
 叫用和 VSPackages 的路由命令的程序與不同的物件執行個體上呼叫方法程序。  
  
 環境傳送命令依序從最內層 \(本機\)\] 指令內容中，根據目前的選取範圍，最外層 \(全域\) 的內容。  也可以執行命令的第一個內容是處理它。  如需詳細資訊，請參閱 [路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
 在大部分的情況下，環境會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  因為命令路由配置，可以讓許多不同的物件來處理命令， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>可以實作任何數目的物件。 其中包括 Microsoft ActiveX 控制項、 視窗檢視實作、 文件物件、 專案階層架構，以及 VSPackage 物件本身 \(適用於全域指令\)。  在某些特殊的情況下，比方說，路由命令 」 在階層中， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必須實作介面。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[實作](../../extensibility/internals/command-implementation.md)|說明如何實作在 VSPackage 中的命令。|  
|[可用性](../../extensibility/internals/command-availability.md)|說明如何 Visual Studio 的內容會決定要使用哪一個指令。|  
|[路由演算法](../../extensibility/internals/command-routing-algorithm.md)|說明如何 Visual Studio 命令路由架構可讓不同的 VSPackages 已經處理過的指令。|  
|[放置指導方針](../../extensibility/internals/command-placement-guidelines.md)|提供如何將命令放在 Visual Studio 的環境中的建議。|  
|[VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|說明如何 VSPackages 可以運用 Visual Studio 指令的架構。|  
|[預設的命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|說明如何 VSPackages 善用 Visual Studio 中所包含的指令。|  
|[管理 Vspackage](../../extensibility/managing-vspackages.md)|說明 Visual Studio 載入 VSPackages 的方式。|  
|[Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供以 XML 為基礎的.vsct 檔案，用來描述的配置和外觀的命令，在 VSPackages 中的相關資訊。|