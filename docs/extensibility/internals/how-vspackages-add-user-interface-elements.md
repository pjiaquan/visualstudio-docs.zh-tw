---
title: "VSPackages 如何新增使用者介面項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6bf44a2b1fa029753c4b3c00f911070a2132bb75
ms.lasthandoff: 02/22/2017

---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackages 如何新增使用者介面項目
新增使用者介面 (UI) 項目，例如，功能表、 工具列和工具視窗，藉由.vsct 檔案的 Visual studio VSPackage。  
  
 您可以找到設計指導方針的 UI 項目在[Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 命令資料表架構  
 如前所述，命令資料表架構支援前述的架構原則。 抽象層，資料結構和工具的命令資料表架構背後的原則如下所示︰  
  
-   有三種基本項目︰ 功能表、 命令和群組。 可在 UI 中公開為功能表中，子功能表、 工具列或工具視窗功能表。 使用者可在 IDE 中執行，就可以公開為功能表項目、 按鈕、 清單方塊或其他控制項的程序的命令。 群組是功能表和命令的容器。  
  
-   描述項目，其優先權，相對於其他項目，並修改其行為的旗標的定義被指定每個項目。  
  
-   每個項目具有描述項目的父代的位置。 項目可以有多個父代，使它可以出現在 UI 中的多個位置。  
  
     每個命令都必須有群組做為其父系，即使它是唯一的子系，該群組中。 每個標準功能表也必須有父群組。 工具列和工具視窗做為其本身的父系。 群組能做為其父代 Visual Studio 功能表列中，或任何功能表、 工具列或工具視窗。  
  
### <a name="how-items-are-defined"></a>如何定義項目  
 .Vsct 檔案是以 XML 格式。 .Vsct 檔會定義封裝的 UI 項目，並決定這些項目出現在 IDE 中的位置。 每個功能表、 群組或封裝中的命令會先指派 GUID 和 ID`Symbols`一節。 .vsct 的其餘檔案、 每個功能表、 命令和群組來識別其 GUID 和 ID 的組合。 下列範例示範典型`Symbols`一節所產生的 Visual Studio 封裝範本時**功能表命令**選取範本中。  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 最上層元素`Symbols`區段是[GuidSymbol 項目](../../extensibility/guidsymbol-element.md)。 `GuidSymbol`元素會對應至 Guid ide 用來識別封裝和其元件部分的名稱。  
  
> [!NOTE]
>  在 Visual Studio 封裝範本自動產生的 Guid。 您可以按一下 建立唯一的 GUID**建立 GUID**上**工具**功能表。  
  
 第一個`GuidSymbol`項目"guid [PackageName] p k g 」，是封裝本身的 GUID。 這是由 Visual Studio 用來載入封裝的 GUID。 一般而言，它並沒有子項目。  
  
 依照慣例，功能表和命令之下的第二個`GuidSymbol`項目"guid [PackageName] CmdSet 」，和點陣圖是在第三個`GuidSymbol`項目，「 guidImages 」。 您沒有遵循此慣例，但每個功能表、 群組、 命令和點陣圖必須是子系`GuidSymbol`項目。  
  
 在第二個`GuidSymbol`項目，它代表封裝命令集，為幾個`IDSymbol`項目。 每個[IDSymbol 元素](../../extensibility/idsymbol-element.md)名稱對應到數值，而且可能呈現功能表、 群組或命令的命令集的一部分。 `IDSymbol`中第三個項目`GuidSymbol`可能做為命令圖示的項目代表點陣圖。 因為 GUID ID 對必須是唯一的應用程式中，沒有相同的兩個子系`GuidSymbol`元素可能具有相同的值。  
  
### <a name="menus-groups-and-commands"></a>功能表、 群組和命令  
 當功能表、 群組或命令具有 GUID 和 ID 時，它會加入到 IDE。 每個 UI 項目必須具有下列事項︰  
  
-   A`guid`屬性符合名稱的`GuidSymbol`UI 項目會定義下的項目。  
  
-   `id`符合相關聯的名稱屬性`IDSymbol`項目。  
  
     在一起，`guid`和`id`屬性撰寫*簽章*UI 項目。  
  
-   A`priority`決定在其父功能表或群組中的 UI 項目位置的屬性。  
  
-   A[父項目](../../extensibility/parent-element.md)具有`guid`和`id`指定父功能表或群組的簽章的屬性。  
  
#### <a name="menus"></a>Menus  
 每個功能表定義為[功能表項目](../../extensibility/menu-element.md)中`Menus`一節。 必須有功能表`guid`， `id`，和`priority`屬性，以及`Parent`項目，也下列的其他屬性和子系︰  
  
-   A`type`屬性來指定在 IDE 的功能表或工具列是否顯示功能表。  
  
-   A[字串項目](../../extensibility/strings-element.md)，其中包含[於項目](../../extensibility/buttontext-element.md)，在 IDE 中，指定功能表的標題和[CommandName 元素](../../extensibility/commandname-element.md)，指定的名稱中使用**命令**視窗來存取功能表。  
  
-   選擇性旗標。 A[命令旗標的項目](../../extensibility/command-flag-element.md)可能會出現在功能表定義以變更其外觀或行為，在 IDE 中的。  
  
 每個`Menu`項目都必須有群組做為其父系，除非它是可停駐的項目，例如工具列。 可停駐的功能表是其本身的父系。 如需有關功能表和值`type`屬性，請參閱[功能表項目](../../extensibility/menu-element.md)文件。  
  
 下列範例顯示旁會出現在 Visual Studio 功能表列的功能表**工具**功能表。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>群組  
 「 群組 」 是定義中的項目`Groups`.vsct 檔的區段。 群組是只是容器。 它們不會出現在 IDE 中除了 功能表上的分隔線。 因此，[群組項目](../../extensibility/group-element.md)由其簽章、 優先權和父代所定義。  
  
 群組可具有和父功能表中，另一個群組，或本身。 不過，父系通常是功能表或工具列。 在前面範例中的功能表是子系`IDG_VS_MM_TOOLSADDINS`群組與該群組是 Visual Studio 功能表列的子系。 下列範例中的群組是功能表的前面範例中的子系。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 因為它是功能表的一部分，這個群組通常會包含命令。 不過，它也可以包含其他功能表。 這是定義子功能表的方式，如下列範例所示。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>命令  
 提供 ide 的命令定義為[Button 元素](../../extensibility/button-element.md)或[下拉式項目](../../extensibility/combo-element.md)。 若要出現在功能表或工具列上，命令必須群組做為其父系。  
  
##### <a name="buttons"></a>按鈕  
 定義按鈕，在`Buttons`一節。 任何功能表項目、 按鈕或其他使用者來執行單一命令的項目會被視為一個按鈕。 某些按鈕類型也可以包含清單功能。 按鈕都有相同的必要和選擇性屬性，有功能表，也會造成[圖示的項目](../../extensibility/icon-element.md)指定的 GUID 和 ID 的點陣圖，表示在 IDE 中的按鈕。 如需按鈕和其屬性的詳細資訊，請參閱[按鈕項目](../../extensibility/buttons-element.md)文件。  
  
 下列範例中的按鈕是在先前範例中，群組的子系，並為該群組的父功能表中的功能表項目會出現在 IDE 中。  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>組合  
 組合中定義`Combos`一節。 每個`Combo`項目代表在 IDE 中的下拉式清單方塊。 清單方塊可能會或可能不是可寫入的值而定的使用者，`type`屬性的組合。 組合具有相同的項目，而按鈕的行為，而且也可以有下列的其他屬性︰  
  
-   A`defaultWidth`屬性來指定像素寬度。  
  
-   `idCommandList`屬性來指定包含的項目會顯示在清單方塊的清單。 必須在同一個宣告命令清單`GuidSymbol`包含組合的節點。  
  
 下列範例會定義下拉式項目。  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>點陣圖  
 將圖示一起顯示的命令必須包含`Icon`項目，點陣圖是指使用其 GUID 和 id。 每個點陣圖定義為[點陣圖元素](../../extensibility/bitmap-element.md)中`Bitmaps`一節。 唯一必要的屬性`Bitmap`定義是`guid`和`href`，指向原始程式檔。 如果原始程式檔的資源區域， **usedList**屬性也是必要的若要列出可用的映像，在區域中。 如需詳細資訊，請參閱[點陣圖元素](../../extensibility/bitmap-element.md)文件。  
  
### <a name="parenting"></a>父代  
 下列規則會管理項目可以呼叫另一個項目做為其父系的方式。  
  
|項目|在本節中的命令資料表定義|可能包含 (父代，或是由放置在`CommandPlacements` 區段中，或兩者)|可能包含 （稱為父代）|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|群組|[群組項目](../../extensibility/groups-element.md)，IDE、 其他 Vspackage|功能表上，一個群組，本身的項目|功能表、 群組和命令|  
|功能表|[功能表項目](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|1 到*n*群組|0 到*n*群組|  
|工具列|[功能表項目](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|項目本身|0 到*n*群組|  
|功能表項目|[按鈕項目](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到*n*群組、 項目本身|-0 到*n*群組|  
|按鈕|[按鈕項目](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到*n*群組、 項目本身||  
|Combo|[組合的項目](../../extensibility/combos-element.md)，IDE、 其他 Vspackage|1 到*n*群組、 項目本身||  
  
### <a name="menu-command-and-group-placement"></a>功能表、 命令和群組放置  
 功能表、 群組或命令可以出現在 IDE 中的多個位置中。 若項目才會出現在多個位置，則必須新增至`CommandPlacements`區段為[CommandPlacement 項目](../../extensibility/commandplacement-element.md)。 可以加入任何功能表、 群組或命令當做命令位置。 不過，工具列無法定位，以這種方式因為不能出現在多個即時線上位置。  
  
 命令位置有`guid`， `id`，和`priority`屬性。 GUID 和 ID 必須符合定位於項目。 `priority`屬性可控制與其他項目之項目的位置。 IDE 會合併兩個或多個具有相同優先順序的項目，其位置時，未定義因為 IDE 並不保證，封裝資源會讀取相同的順序建置封裝每次。  
  
 如果功能表或群組出現在多個位置，該功能表或群組的所有子系會出現在每個執行個體。  
  
## <a name="command-visibility-and-context"></a>命令的可見性和內容  
 多個 VSPackages 安裝時，功能表、 功能表項目和工具列不易可能弄亂 IDE。 若要避免這個問題，您可以控制個別的 UI 項目的可見性，使用*的可視性約束*和命令旗標。  
  
##### <a name="visibility-constraints"></a>可見性條件約束  
 可見性條件約束設定為[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)中`VisibilityConstraints`一節。 可見性條件約束定義的目標項目會顯示特定 UI 內容。 功能表或包含在此區段中的命令可見時才會定義內容的其中一個使用中。 如果這一節中未參考的功能表或命令，經常會預設為可見。 本節不會套用至群組。  
  
 `VisibilityItem`項目必須有三種屬性，如下所示︰`guid`和`id`目標 UI 項目和`context`。 `context`屬性會指定當目標項目將會顯示，並接受任何有效的 UI 內容做為其值。 Visual Studio 的 UI 內容常數屬於成員的<xref:Microsoft.VisualStudio.VSConstants>類別。</xref:Microsoft.VisualStudio.VSConstants> 每個`VisibilityItem`項目可能只有一個內容值。 若要套用第二個內容，建立第二個`VisibilityItem`指向相同的項目，如下列範例所示的項目。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>命令旗標  
 下列的命令旗標可能會影響功能表和命令就會套用到的可見性。  
  
 AlwaysCreate  
 它在沒有任何群組或按鈕，已建立功能表。  
  
 適用於︰`Menu`  
  
 CommandWellOnly  
 套用此旗標命令不會出現在最上層功能表，而且您想要使其可供其他 shell 自訂項目，例如，繫結至索引鍵。 VSPackage 安裝之後，使用者可以自訂這些命令開啟**選項**] 對話方塊中，然後編輯 [命令位置下的**鍵盤環境**類別。 不會影響快顯功能表、 工具列、 功能表控制器或子功能表上的位置。  
  
 適用於︰ `Button`，`Combo`  
  
 DefaultDisabled  
 根據預設，如果未載入 VSPackage 實作命令，或尚未呼叫 QueryStatus 方法，會停用命令。  
  
 適用於︰ `Button`，`Combo`  
  
 DefaultInvisible  
 根據預設，此命令為不可見，如果未載入 VSPackage 實作命令，或尚未呼叫 QueryStatus 方法。  
  
 應該要結合`DynamicVisibility`旗標。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 使用 QueryStatus 方法或內容中所包含的 GUID 也可以變更命令的可見性`VisibilityConstraints`一節。  
  
 適用於出現在功能表中，不會在工具列上的命令。 最上層工具列項目可以停用，但不是能隱藏 OLECMDF_INVISIBLE 旗標從 QueryStatus 方法傳回時。  
  
 在功能表上，這個旗標也會指出，它應該會自動隱藏隱藏其成員時。 這個旗標通常會指派給子功能表，因為最上層功能表已經有這個行為。  
  
 應該要結合`DefaultInvisible`旗標。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 如果這個旗標的命令位於功能表控制站上，命令不會不會出現在下拉式清單中。  
  
 適用於︰`Button`  
  
 如需命令旗標的詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)文件。  
  
##### <a name="general-requirements"></a>一般需求  
 顯示並啟用之前，命令必須通過一系列如下的測試︰  
  
-   此命令是正確的位置。  
  
-   `DefaultInvisible`未設定旗標。  
  
-   父功能表或工具列為可見。  
  
-   此命令不是不可見因為在內容項目而[VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)一節。  
  
-   VSPackage 實作的程式碼<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面顯示，並讓您的命令。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 沒有介面程式碼攔截它，並在其上動作。  
  
-   當使用者按一下您的命令時，它受到中概述的程序[路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="calling-pre-defined-commands"></a>呼叫預先定義的命令  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)VSPackages 可讓您存取其他 VSPackages 或 IDE 所提供的命令。 若要這樣做，請建立[UsedCommand 元素](../../extensibility/usedcommand-element.md)具有 GUID 並使用命令識別碼。 這可確保命令將會載入由 Visual Studio 中，即使它不是目前的 Visual Studio 組態的一部分。 如需詳細資訊，請參閱[UsedCommand 項目](../../extensibility/usedcommand-element.md)。  
  
## <a name="interface-element-appearance"></a>介面項目外觀  
 選取和定位命令元素的考量如下︰  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供顯示的方式會根據放置許多 UI 項目。  
  
-   UI 項目所定義的使用`DefaultInvisible`旗標不會顯示在 IDE 中是顯示在由它的 VSPackage 實作，除非<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法，或在特定的 UI 內容相關聯`VisibilityConstraints`一節。</xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>  
  
-   不會顯示成功定位的命令。 這是因為 IDE 會自動隱藏或顯示一些命令，根據 VSPackage 具有 （或沒有） 的介面實作。 比方說，VSPackage 實作一些建置介面會自動顯示的原因與組建相關的功能表項目。  
  
-   套用`CommandWellOnly`的 UI 項目定義中的旗標表示命令可以新增只能由自訂。  
  
-   當 IDE 在設計檢視，顯示對話方塊時，才可能僅適用於特定 UI 內容，例如，命令。  
  
-   若要使特定的 UI 項目顯示在 IDE 中，您必須實作一個或多個介面，或撰寫一些程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)
