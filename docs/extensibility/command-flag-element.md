---
title: "命令旗標的項目 | Microsoft Docs"
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
  - "CommandFlag 項目 (VSCT XML 結構描述)"
  - "CommandFlag，VSCT XML 結構描述項目"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令旗標的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

修改其父項目。  
  
## 語法  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## 屬性和項目  
 下節將說明有效的項目值。  
  
### 屬性  
 無。  
  
### 子項目  
  
|值|描述|  
|-------|--------|  
|AllowParams|表示使用者可以輸入中的命令參數 **命令** 他們輸入命令的標準名稱時，視窗。<br /><br /> 適用於: `Button`|  
|AlwaysCreate|它在沒有任何群組或按鈕，已建立功能表。<br /><br /> 適用於: `Menu`|  
|CaseSensitive|使用者項目是區分大小寫。<br /><br /> 適用於: `Combo`|  
|CommandWellOnly|如果命令不會出現在最上層功能表，而且您想要使其可供其他殼層自訂，例如，針對繫結至鍵盤快速鍵，請套用此旗標。 VSPackage 安裝之後，您可以自訂這些命令開啟 **選項** \] 對話方塊中，然後編輯 \[命令位置下的 **鍵盤環境** 類別。 這個旗標不會影響快顯功能表、 工具列、 功能表控制器或子功能表上的位置。<br /><br /> 適用於: `Button`, ，`Combo`|  
|DefaultDisabled|根據預設，已停用命令如果未載入 VSPackage 實作它或 `QueryStatus` 尚未呼叫方法。<br /><br /> 適用於: `Button`, ，`Combo`|  
|DefaultDocked|依預設停駐。 此設定不會再套用至工具列，因為一律停駐。|  
|DefaultInvisible|根據預設，命令不會察覺，如果未載入 VSPackage 實作它或 `QueryStatus` 尚未呼叫方法。<br /><br /> 我們建議您將其與 `DynamicVisibility` 旗標。<br /><br /> 適用於: `Button`, ，`Combo`, ，`Menu`|  
|DontCache|在開發環境並不會快取 `QueryStatus` 方法的結果，此命令。<br /><br /> 功能表中，這會告訴功能表控制器不是用來快取其功能表項目的文字。 該功能表包含動態項目或動態文字的項目時，請使用這個旗標。<br /><br /> 適用於: `Button`, ，`Menu`|  
|DynamicItemStart|表示動態清單的開頭。 這可讓環境建立的清單，藉由連續呼叫 `QueryStatus` 方法，直到傳回 OLECMDERR\_E\_UNSUPPORTED 旗標的清單項目上。 這適用於項目，例如最近使用的 \(MRU\) 清單及視窗清單。<br /><br /> 適用於: `Button`|  
|DynamicVisibility|此命令的可見性可以透過變更 `QueryStatus` 方法或透過在內容中所包含的 GUID `VisibilityConstraints` 一節。<br /><br /> 適用於顯示功能表和工具視窗工具列中，而不是會出現在主視窗的最上層工具列上的命令。 最上層工具列項目可以停用，但並未隱藏，請從傳回 OLECMDF\_INVISIBLE 旗標時 `QueryStatus` 方法。 可以隱藏工具視窗工具列顯示的工具列命令。<br /><br /> 在功能表上，這個旗標也會指出，它應該會自動隱藏隱藏其所有成員時。 這個旗標通常會指派給子功能表，因為最上層功能表已經有這個行為。<br /><br /> 這個旗標應該要結合 `DefaultInvisible` 旗標。<br /><br /> 適用於: `Button`, ，`Combo`, ，`Menu`|  
|篩選鍵|請參閱 \> 底下的篩選鍵主題 [下拉式項目](../extensibility/combo-element.md)。<br /><br /> 適用於: `Combo`|  
|FixMenuController|此命令位於功能表控制站上，如果命令永遠都是預設值。也就被選取之功能表控制器按鈕本身時，會選取命令。 如果功能表控制 `TextIsAnchorCommand` 旗標集，則功能表控制器也會採用其文字的命令，從 `FixMenuController` 旗標。<br /><br /> 功能表控制站上的只能有一個命令應有 `FixMenuController` 旗標。 如果如此標示一個以上的命令，在功能表中的最後一個命令會變成預設命令。<br /><br /> 適用於: `Button`|  
|IconAndText|功能表和工具列上顯示的圖示和文字。<br /><br /> 適用於: `Button`, ，`Combo`, ，`Menu`|  
|NoAutoComplete|已停用自動完成功能。<br /><br /> 適用於: `Combo`|  
|NoButtonCustomize|不要讓使用者可以自訂此按鈕。<br /><br /> 適用於: `Button`, ，`Combo`|  
|NoKeyCustomize|請勿啟用鍵盤自訂。<br /><br /> 適用於: `Button`, ，`Combo`|  
|NoShowOnMenuController|如果這個命令位於功能表控制站上，命令並不會顯示在下拉式清單。<br /><br /> 適用於: `Button`|  
|NotInTBList|不會顯示在 \[可用工具列的清單。 這是只適用於工具列功能表類型。<br /><br /> 適用於: `Menu`|  
|NoToolbarClose|使用者無法關閉工具列。 這是只適用於工具列功能表類型。<br /><br /> 適用於: `Menu`|  
|Pict|只有圖示顯示在工具列上，但只在功能表上的文字。 如果指定的圖示，顯示可點按的空白區域工具列上。<br /><br /> 適用於: `Button`|  
|PostExec|可讓命令未封鎖。 在開發環境會延後執行，直到完成所有前置處理查詢。<br /><br /> 適用於: `Button`|  
|RouteToDocs|此命令會路由至使用中文件。<br /><br /> 適用於: `Button`|  
|StretchHorizontally|當設定這個旗標時，寬度會變成下拉式方塊的最小寬度，若是在工具列上的空間，下拉式方塊會自動延伸以填滿可用空間。 會發生這種情況只有在水平工具列，而且在工具列上的一個下拉式方塊可以使用旗標 \(旗標會忽略所有除了第一個下拉式方塊\)。<br /><br /> 適用於: `Combo`|  
|TextMenuUseButton|使用 `ButtonText` 欄位功能表。 預設欄位是 `MenuText` 如果有指定。<br /><br /> 適用於: `Button`|  
|文字變更|命令或功能表變更的文字可以在執行階段，通常透過 `QueryStatus` 方法。<br /><br /> 適用於: `Button`, ，`Menu`|  
|TextChangesButton|適用於: `Button`|  
|TextIsAnchorCommand|功能表控制站\] 功能表上的文字是取自預設 \(錨定\) 命令。 錨定命令是選取或閂鎖的最後一個命令。 如果未設定此旗標，功能表控制器會使用它自己 `MenuText` 欄位。 不過，按一下功能表上的控制站仍然會啟用所選取的最後一個命令，從該控制器。<br /><br /> 我們建議您結合使用這個旗標 `TextChanges` 旗標。<br /><br /> 這個旗標僅適用於類型的功能表 MenuController 或 MenuControllerLatched。<br /><br /> 適用於: `Menu`|  
|TextMenuCtrlUseMenu|使用 `MenuText` 功能表控制站上的欄位。 預設欄位是 `ButtonText`。<br /><br /> 適用於: `Button`|  
|TextMenuUseButton|使用 `ButtonText` 欄位功能表。 預設欄位是 `MenuText` 如果有指定。<br /><br /> 適用於: `Button`|  
|TextOnly|只會顯示文字的工具列或功能表上，但沒有圖示即使指定圖示。<br /><br /> 適用於: `Button`|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[按鈕項目](../extensibility/buttons-element.md)|提供的群組 [Button 元素](../extensibility/button-element.md) 項目。|  
|[功能表項目](../extensibility/menus-element.md)|定義所有 VSPackage 實作的功能表。|  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)