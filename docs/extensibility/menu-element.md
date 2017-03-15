---
title: "功能表項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 結構描述項目功能表"
  - "功能表項目 (VSCT XML 結構描述)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 功能表項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義一個功能表項目。 這些是功能表的六種: 內容、 功能表、 MenuController、 MenuControllerLatched、 工具列和 ToolWindowToolbar。  
  
## 語法  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 GUID ID 的命令識別項的 GUID。|  
|id|必要項。 GUID ID 的命令識別項的識別碼。|  
|priority|選擇項。 數值，指定群組中的功能表的功能表中的相對位置。|  
|ToolbarPriorityInBand|選擇項。 數值，停駐視窗時，群組列中指定工具列的相對位置。|  
|類型|選擇項。 列舉的值，指定元素的類型。<br /><br /> 如果不存在，此預設類型為功能表。<br /><br /> 內容<br /> 當使用者按一下滑鼠右鍵視窗會顯示快顯功能表。 快顯功能表具有下列特性:<br /><br /> -   不使用父代和優先權欄位，顯示為快顯功能表的功能表時。<br />-   可當做子功能表，為快顯功能表。 在此情況下，必須遵守群組識別碼\] 和 \[優先順序\] 欄位。<br />-   並非永遠可用。<br /><br /> 只有當下列條件成立時，會顯示快顯功能表:<br /><br /> -   主控視窗隨即顯示。<br />-   滑鼠處理常式在 VSPackage 中的偵測到視窗上的按一下滑鼠右鍵，然後再呼叫處理命令的方法。<br />-   快顯功能表會顯示藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 方法 \(建議方法\) 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 方法。<br /><br /> 功能表<br /> 提供下拉式選單。 下拉式選單中具有下列特性:<br /><br /> -   會遵守其定義中的父系。<br />-   必須有父群組或 CommandPlacement 至群組。<br />-   可以是功能表的任何其他種類中的子功能表。<br />-   會自動顯示其父功能表顯示時。<br />-   不需要任何 VSPackage 程式碼，使其顯示的實作。<br /><br /> MenuController<br /> 提供分割按鈕的下拉式選單，通常用於在工具列中。 MenuController 功能表具有下列特性:<br /><br /> -   必須包含在父代或 CommandPlacement 透過另一個功能表。<br />-   會遵守其定義中的父系。<br />-   任何一種功能表可做為其父系。<br />-   會自動可供其父功能表顯示時。<br />-   不需要程式設計的支援，讓顯示的功能表。<br /><br /> 從分割\] 按鈕功能表命令會顯示在 \[功能表\] 按鈕。 顯示命令有下列特性的其中一個:<br /><br /> -   它是最後一個命令仍會顯示，並且啟用，如果使用的命令。<br />-   它是第一個顯示的命令。<br /><br /> MenuControllerLatched<br /> 提供分割按鈕下拉式選單中的命令可以指定為預設選取項目所標示為閂鎖的命令。<br /><br /> 鎖住的命令是通常顯示核取記號標示為已選取，功能表中的命令。 命令可標示為閂鎖是否 OLECMDF\_LATCHED 旗標設在其上實作的 `QueryStatus` 方法 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 MenuControllerLatched 功能表具有下列特性:<br /><br /> -   必須包含在父群組或 CommandPlacement 透過另一個功能表。<br />-   會遵守其定義中的父系。<br />-   任何一種功能表可做為其父系。<br />-   可顯示其父功能表時。<br />-   不需要程式設計的支援，讓顯示的功能表。<br /><br /> 從分割\] 按鈕功能表命令會顯示在 \[功能表\] 按鈕。 顯示命令有下列特性的其中一個:<br /><br /> -   它是第一個閂鎖的顯示的命令。<br />-   它是第一個顯示的命令。<br /><br /> 工具列<br /> 提供的工具列。 工具列上有下列特性:<br /><br /> -   會忽略其定義中的父系。<br />-   無法透過子功能表中的任何群組，甚至不使用 CommandPlacement。<br />-   一律會顯示依序按一下 **工具列** 上 **檢視** 功能表。<br />-   可以使用顯示 [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis)。<br />-   不需要任何程式碼來建立它。 如需有關如何建立工具列，請參閱 [新增工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 提供附加到特定的工具視窗、 工具列，工具列會附加至開發環境一樣。<br /><br /> -   會忽略其定義中的父系。<br />-   無法透過子功能表中的任何群組，甚至不使用 CommandPlacement。<br />-   工具視窗裝載工具列會顯示和 VSPackage 明確地將工具列新增至 \[工具\] 視窗時，才會顯示。 這通常是透過取得工具列主機內容建立工具視窗時 \(所表示的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 介面\) 的工具視窗框架，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 方法。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|父代|選擇項。 功能表項目的父項目。|  
|CommandFlag|必要項。 請參閱 [命令旗標的項目](../extensibility/command-flag-element.md)。 功能表的 CommandFlag 有效值如下所示:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-這個旗標不會影響顯示的工具列。<br />-   **DontCache**<br />-   **DynamicVisibility** \-這個旗標不會影響顯示的工具列。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **文字變更**<br />-   **TextIsAnchorCommand**|  
|字串|必要項。 請參閱 [字串的項目](../extensibility/strings-element.md)。 子系 `ButtonText` 必須定義項目。|  
|註釋|選擇性註解。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[功能表項目](../extensibility/menus-element.md)|定義所有 VSPackage 實作的功能表。|  
  
## 範例  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)