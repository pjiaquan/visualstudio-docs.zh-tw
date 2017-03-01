---
title: "CommandTable 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
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
ms.openlocfilehash: 4a6abf25d0e3eff335c8a6fe62affc19d8037afa
ms.lasthandoff: 02/22/2017

---
# <a name="commandtable-element"></a>CommandTable 項目
CommandTable 是.vsct 檔的根項目。 這是定義的實際配置和 VSPackage 會提供 IDE 的命令類型的檔案。 命令可能包括功能表項目、 功能表、 工具列和下拉式方塊。 如需詳細資訊，請參閱[Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|xmlns|必要項。 XML 命名空間︰<br /><br /> xmlns ="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs ="http://www.w3.org/2001/XMLSchema"|  
|語言|選擇項。 [語言] 屬性可用來指定所有的預設語言\<字串 > 中的命令資料表的項目。  如果未指定語言，將會使用目前的處理序的語言︰<br /><br /> 語言 ="en-我們 」|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Extern 項目](../extensibility/extern-element.md)|選擇項。 包含編譯器前置處理器指示詞。|  
|[包含項目](../extensibility/include-element.md)|選擇項。 包含任何要包含在編譯中的檔案路徑。|  
|[定義項目](../extensibility/define-element.md)|選擇項。 定義指定其名稱和值的符號。|  
|[Commands 元素](../extensibility/commands-element.md)|選擇項。 父項目定義的所有命令的 VSPackage，其中包含所有其他項目。|  
|[CommandPlacements 項目](../extensibility/commandplacements-element.md)|選擇項。 定義命令列命令的位置放置。|  
|[VisibilityConstraints 項目](../extensibility/visibilityconstraints-element.md)|選擇項。 決定命令和工具列的靜態的可見性。|  
|[按鍵組合的項目](../extensibility/keybindings-element.md)|選擇項。 快速鍵組合，如果指定任何命令。|  
|[UsedCommands 項目](../extensibility/usedcommands-element.md)|選擇項。 可選擇性地實作自己的版本，其他 VSPackages 原本支援的功能的 VSPackage。|  
|[符號的項目](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|選擇項。 包含的所有符號資料-Guid、 識別碼和其他等等-編譯器。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
