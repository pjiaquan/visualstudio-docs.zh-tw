---
title: "[撰寫中。Vsct 檔案 | Microsoft Docs"
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
  - "VSCT 檔案，手動撰寫"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# [撰寫中。Vsct 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本文件說明如何撰寫.vsct 檔加入 Visual Studio 整合式的開發環境 \(IDE\) 中的功能表項目、 工具列和其他使用者介面 \(UI\) 項目。 當您將 UI 項目加入至 Visual Studio 套件 \(VSPackage\) 已經沒有.vsct 檔，請使用下列步驟。  
  
 針對新的專案，我們建議您使用 Visual Studio 封裝範本，因為它會產生.vsct 檔，根據您的選擇，已經有必要的項目，功能表命令、 工具視窗，或自訂編輯器。 您可以修改此.vsct 檔案，以符合需求的 VSPackage。 如需如何修改.vsct 檔的詳細資訊，請參閱中的範例 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## 撰寫的檔案  
 撰寫.vsct 檔中這三個階段: 建立檔案和資源的結構、 宣告的 UI 項目、 將 UI 項目放在 IDE 中，並加入任何特殊的行為。  
  
### 檔案結構  
 .Vsct 檔的基本結構是 [CommandTable](../../extensibility/commandtable-element.md) 根項目，其中包含 [命令](../../extensibility/commands-element.md) 項目和 [符號](../../extensibility/symbols-element.md) 項目。  
  
##### 若要建立的檔案結構  
  
1.  .vsct 將檔案新增至您的專案中的步驟 [如何: 建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。  
  
2.  加入必要的命名空間 `CommandTable` 元素，如下列範例所示。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  在 `CommandTable` 項目，加入 `Commands` 裝載自訂功能表、 工具列、 命令群組和命令的所有項目。 這樣可以載入自訂的 UI 項目， `Commands` 項目必須具有其 `Package` 屬性設為封裝的名稱。  
  
     之後 `Commands` 項目，加入 `Symbols` 項目來定義封裝和名稱的 Guid，以及 UI 項目的命令 Id。  
  
### 包括 Visual Studio 資源  
 使用 [Extern](../../extensibility/extern-element.md) 項目來存取定義 Visual Studio 命令和功能表在 IDE 中放入您的 UI 項目所需的檔案。 如果您將使用您的封裝外部所定義的命令，使用 [UsedCommands](../../extensibility/usedcommands-element.md) 通知 Visual Studio 的項目。  
  
##### 包含 Visual Studio 資源  
  
1.  在頂端 `CommandTable` 項目，加入一個 `Extern` 項目，每個外部檔案參考，並設定 `href` 屬性設定為檔案的名稱。 您可以參考下列標頭檔來存取 Visual Studio 資源:  
  
    -   Stdidcmd.h，Visual Studio 所公開的所有命令定義識別碼。  
  
    -   Vsshlids.h，包含 Visual Studio 功能表的命令識別碼。  
  
2.  如果您的封裝呼叫 Visual Studio 或其他封裝所定義的任何命令，將新增 `UsedCommands` 項目之後 `Commands` 項目。 填入此項目 [UsedCommand](../../extensibility/usedcommand-element.md) 項目，每個命令呼叫也就不是屬於您的封裝。 設定 `guid` 和 `id` 屬性 `UsedCommand` 呼叫命令的 GUID 和 ID 值的項目。 如需如何尋找 Guid 和 Id Visual Studio 的 \[命令的詳細資訊，請參閱 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要從其他封裝呼叫命令，使用 GUID 和命令，這些封裝的.vsct 檔中所定義的識別碼。  
  
### 宣告 UI 項目  
 將所有新的 UI 項目中宣告 `Symbols` .vsct 檔的區段。  
  
##### 若要宣告 UI 項目  
  
1.  在 `Symbols` 項目，將三個 [GuidSymbol](../../extensibility/guidsymbol-element.md) 項目。 每個 `GuidSymbol` 項目具有 `name` 屬性和 `value` 屬性。 設定 `name` 屬性，讓它反映出之項目的用途。`value` 屬性會取得 GUID。 \(在產生的 GUID， **工具** \] 功能表上，按一下 \[ **建立 GUID**, ，然後選取 **登錄格式**。\)  
  
     第一個 `GuidSymbol` 項目代表您的封裝，且通常沒有子系。 第二個 `GuidSymbol` 元素代表命令集，並將包含所有定義您的功能表、 群組和命令的符號。 第三個 `GuidSymbol` 項目代表您的映像存放區，並且包含所有命令圖示的符號。 如果您有沒有使用圖示的命令，您可以省略第三個 `GuidSymbol` 項目。  
  
2.  在 `GuidSymbol` 項目，表示您的命令集，新增一或多個 [IDSymbol](../../extensibility/idsymbol-element.md) 項目。 每一種代表功能表、 工具列、 群組或您要加入至 UI 的命令。  
  
     每個 `IDSymbol` 元素中，將 `name` 屬性設定為您的名稱會用來參考對應的功能表、 群組或命令，然後設定 `value` 十六進位數字表示其命令 id 的項目。 任兩個 `IDSymbol` 有相同的父代的項目可以有相同的值。  
  
3.  如果任何 UI 項目需要圖示，將 `IDSymbol` 到每個圖示的項目 `GuidSymbol` 項目，表示您的映像存放區。  
  
### 將 UI 項目放在 IDE 中  
 [功能表](../../extensibility/menus-element.md) 項目， [群組](../../extensibility/groups-element.md) 項目，以及 [按鈕](../../extensibility/buttons-element.md) 項目包含所有的功能表、 群組和您的封裝中定義的命令定義。 將這些功能表、 群組和命令放在 IDE 中使用 [父](../../extensibility/parent-element.md) 項目，這是部分 UI 項目定義，或使用 [CommandPlacement](../../extensibility/commandplacement-element.md) 項目，是定義在其他位置。  
  
 每個 `Menu`, ，`Group`, ，和 `Button` 項目具有 `guid` 屬性和 `id` 屬性。 一定會設定 `guid` 屬性，以符合名稱 `GuidSymbol` 項目，表示您的命令集，並設定 `id` 屬性的名稱為 `IDSymbol` 項目，表示您的功能表、 群組或在命令 `Symbols` 一節。  
  
##### 若要定義 UI 項目  
  
1.  如果您要定義任何新的功能表、 子功能表、 捷徑功能表或工具列，加入 `Menus` 項目 `Commands` 項目。 然後，針對要建立每個功能表上，新增 [功能表](../../extensibility/menu-element.md) 項目 `Menus` 項目。  
  
     設定 `guid` 和 `id` 屬性 `Menu` 項目，並將其設定 `type` 屬性設定為想要的類型。 您也可以設定 `priority` 屬性，以建立父群組中的功能表上的相對位置。  
  
    > [!NOTE]
    >  `priority` 屬性不適用於工具列和快顯功能表。  
  
2.  在 Visual Studio IDE 中的所有命令必須直接子系的功能表和工具列命令群組所都裝載。 如果您要新增新的功能表或工具列為 IDE，這些資料表必須包含新的命令群組。 您也可以新增至現有的功能表和工具列命令群組，以便您可以以視覺方式群組您的命令。  
  
     當您新增新的命令群組時，您必須先建立 `Groups` 項目，然後將它加入 [群組](../../extensibility/group-element.md) 針對每個命令群組的項目。  
  
     設定 `guid` 和 `id` 各自屬性 `Group` 項目，並將其設定 `priority` 屬性，以建立父功能表上的群組的相對位置。 如需詳細資訊，請參閱[建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
3.  如果您要在 IDE 中加入新的命令，將新增 `Buttons` 項目 `Commands` 項目。 然後，針對每個命令中，新增 [按鈕](../../extensibility/button-element.md) 項目 `Buttons` 項目。  
  
    1.  設定 `guid` 和 `id` 各自屬性 `Button` 項目，並將其設定 `type` 屬性設定為想要的按鈕類型。 您也可以設定 `priority` 屬性，以建立父群組中的相對位置的命令。  
  
        > [!NOTE]
        >  使用 `type="button"` 標準功能表命令和工具列上的按鈕。  
  
    2.  在 `Button` 項目，加入 [字串](../../extensibility/strings-element.md) 包含項目 [ButtonText](../../extensibility/buttontext-element.md) 項目和 [CommandName](../../extensibility/commandname-element.md) 項目。`ButtonText` 項目提供的功能表項目或工具列按鈕的工具提示文字標籤。`CommandName` 項目會提供要在命令中使用命令的名稱。  
  
    3.  如果您的命令將會有一個圖示，建立 [圖示](../../extensibility/icon-element.md) 中的項目 `Button` 項目，並將其 `guid` 和 `id` 屬性，將 `Bitmap` 圖示的項目。  
  
        > [!NOTE]
        >  工具列按鈕必須圖示。  
  
     如需詳細資訊，請參閱[MenuCommand 對比 OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)。  
  
4.  如果您的命令的任何需要圖示，將 [點陣圖](../../extensibility/bitmaps-element.md) 項目 `Commands` 項目。 然後，針對每個圖示，將 [點陣圖](../../extensibility/bitmap-element.md) 項目 `Bitmaps` 項目。 這是您用來指定點陣圖資源的位置。 如需詳細資訊，請參閱[將圖示加入至功能表命令](../../extensibility/adding-icons-to-menu-commands.md)。  
  
 您可以依賴正確放置大部分的功能表、 群組和命令的父結構。 對於非常大的命令集，或當功能表、 群組或命令必須出現在多個位置中，我們建議您指定命令的位置。  
  
##### 仰賴 UI 項目放置在 IDE 中的父  
  
1.  對於典型的父建立 `Parent` 中每個項目 `Menu`, ，`Group`, ，和 `Command` 您封裝中定義的項目。  
  
     目標的 `Parent` 項目是功能表或群組將包含功能表、 群組或命令。  
  
    1.  設定 `guid` 屬性的名稱為 `GuidSymbol` 定義的命令集的項目。 如果目標項目不是套件的一部分，使用 guid 的命令集，對應.vsct 檔中所定義。  
  
    2.  設定 `id` 屬性，以符合 `id` 目標\] 功能表或群組的屬性。 功能表和 Visual Studio 所公開的群組清單，請參閱 [Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 或 [Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。  
  
 如果您有大量的 UI 項目放置在 IDE 中，或如果您有多個位置中應該會出現的項目，定義其放置在 [CommandPlacements](../../extensibility/commandplacements-element.md) 項目，如下列步驟中所示。  
  
##### 若要將 UI 項目放置在 IDE 中使用命令位置  
  
1.  之後 `Commands` 項目，加入 `CommandPlacements` 項目。  
  
2.  在 `CommandPlacements` 項目，加入 `CommandPlacement` 的每個功能表、 群組或命令將項目。  
  
     每個 `CommandPlacement` 項目或 `Parent` 項目會將一個功能表、 群組或命令放在一個 IDE 的位置。 UI 項目只能有一個父代，但也可能會有多個命令的位置。 若要將 UI 項目放在多個位置中，加入 `CommandPlacement` 針對每個位置的項目。  
  
3.  設定 `guid` 和 `id` 各自屬性 `CommandPlacement` 項目，裝載的功能表或群組，就像您一樣 `Parent` 項目。 您也可以設定 `priority` 屬性，以建立 UI 項目相對的位置。  
  
 您可以混合放置的父和命令的位置。 不過，對於非常大的命令集，我們建議您使用只命令的位置。  
  
### 加入特殊的行為  
 您可以使用 [CommandFlag](../../extensibility/command-flag-element.md) 項目來修改行為的功能表和命令，例如，若要變更其外觀和可見性。 命令會顯示使用時，也可能影響 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), ，或藉由加入鍵盤快速鍵 [按鍵組合](../../extensibility/keybindings-element.md)。 功能表和命令已經特定種類的特殊內建的行為。  
  
##### 若要新增特定的行為  
  
1.  若要顯示的 UI 項目只在特定 UI 內容，例如，在載入方案時，使用可見性條件約束。  
  
    1.  之後 `Commands` 項目，加入 `VisibilityConstraints` 項目。  
  
    2.  若要限制每個 UI 項目，將 [VisibilityItem](../../extensibility/visibilityitem-element.md) 項目。  
  
    3.  每個 `VisibilityItem` 元素中，將 `guid` 和 `id` 屬性給功能表、 群組，或命令，並將其設定 `context` 屬性至您想，UI 內容中所定義 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 類別。 如需詳細資訊，請參閱[VisibilityItem 項目](../../extensibility/visibilityitem-element.md)。  
  
2.  若要在程式碼中設定的可見性或可用性的 UI 項目，使用一或多個下列的命令旗標:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
3.  若要變更項目出現時，或以動態方式變更其外觀的方式，使用一或多個下列的命令旗標:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   Pict  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   文字變更  
  
    -   TextOnly  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
4.  若要變更項目做出反應接收命令時，使用一或多個下列的命令旗標:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   篩選鍵  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
5.  若要附加功能表相關的快速鍵功能表或功能表上的項目，將連字號字元 \('& '\) 在 `ButtonText` 項目\] 功能表或功能表項目。 在父功能表開啟時，後面連字號的字元是作用中的鍵盤快速鍵。  
  
6.  若要命令連接獨立於功能表上的鍵盤快速鍵，請使用 [按鍵組合](../../extensibility/keybindings-element.md)。 如需詳細資訊，請參閱[KeyBinding 項目](../../extensibility/keybinding-element.md)。  
  
7.  若要當地語系化功能表文字，請使用 `LocCanonicalName` 項目。 如需詳細資訊，請參閱[字串的項目](../../extensibility/strings-element.md)。  
  
 某些功能表和按鈕的類型包括特殊的行為。 下表描述一些特殊的功能表和按鈕類型。 對於其他類型，請參閱 `types` 屬性中的描述 [功能表項目](../../extensibility/menu-element.md), ，[Button 元素](../../extensibility/button-element.md), ，和 [下拉式項目](../../extensibility/combo-element.md)。  
  
 下拉式方塊  
 下拉式方塊是可以使用工具列的下拉式清單。 若要加入下拉式方塊的 ui，建立 [組合](../../extensibility/combos-element.md) 中的項目 `Commands` 項目。 然後加入 `Combos` 元素 `Combo` 每個組合中加入的項目。`Combo` 元素具有相同的屬性和子系為 `Button` 項目，也有 `DefaultWidth` 和 `idCommandList` 屬性。`DefaultWidth` 屬性設定為像素的寬度和 `idCommandList` 屬性指向用來填入下拉式方塊的命令 ID。 如需詳細資訊，請參閱 `Combo` 項目的文件。  
  
 MenuController  
 功能表控制器是具有該索引標籤旁邊的箭號按鈕。 按一下箭頭，即可開啟清單。 若要加入功能表控制器 ui，建立 `Menu` 項目並設定其 `type` 屬性設定為 **MenuController** 或 **MenuControllerLatched**, ，取決於您要的行為。 若要填入功能表控制站，將它設為父代 `Group` 項目。 功能表控制器將會顯示該群組的所有子系的下拉式清單上。  
  
## 請參閱  
 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)