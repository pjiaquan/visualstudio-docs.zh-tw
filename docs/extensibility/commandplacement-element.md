---
title: "CommandPlacement 項目 | Microsoft Docs"
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
  - "CommandPlacements 項目 (VSCT XML 結構描述)"
  - "CommandPlacements，VSCT XML 結構描述項目"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# CommandPlacement 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

要包含在一個以上的群組或功能表中的按鈕、 群組和功能表，可讓 CommandPlacement 項目。 藉由使用 CommandPlacement 項目，您不需要完全重新定義這些項目，以便用來修改使用者介面的外觀。  
  
 如需詳細資訊，請參閱[建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
## 語法  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 中所定義的命令集的 guid [符號的項目](../extensibility/symbols-element.md)。|  
|id|必要項。 功能表、 群組或放置中, 所定義的命令識別碼 `Symbols Element`。|  
|priority|必要項。 決定 visual 位置的項目在其父項目。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|父代|必要項。 功能表或裝載要放置項目群組。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandPlacements 項目](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 項目群組。|  
  
## 範例  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## 請參閱  
 [CommandPlacements 項目](../extensibility/commandplacements-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)