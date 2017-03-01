---
title: "預設命令、 群組及工具列位置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
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
ms.openlocfilehash: 1d418eea04791d85dd0e8d08fba23abe8dc7e054
ms.lasthandoff: 02/22/2017

---
# <a name="default-command-group-and-toolbar-placement"></a>預設的命令、 群組及工具列位置
如需產品的一致性和穩定性，UI 預設會顯示特定命令群組，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供定義命令和命令群組。 標準命令和命令群組，也可以使用 Vspackage。  
  
 預設命令群組分成三大類︰ IDE 命令、 產品命令和編輯器命令。  
  
## <a name="default-ide-commands"></a>預設 IDE 命令  
 預設 IDE 工具列包含共用的所有產品中所包含的命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 這些包括相關專案的一般作業，例如指令**儲存**命令和**加入項目**命令。 VSPackages 不應該加入或減去此工具列，但有一個例外︰ 如果產品或 VSPackage 加入新的工具視窗中，則視窗應加入至可用的工具視窗的清單，在**檢視**功能表。 新產品或 VSPackages 可以加入自己的工具列。  
  
## <a name="default-product-commands"></a>預設產品命令  
 每項產品可以提供自己預設工具列，其中包含重要且常用命令的 IDE。 它是最好的方式，不過，使用現有的功能表和工具列盡可能並補足和其他特定工作所需。  
  
 工具列的 [優先順序] 欄位會決定它的資料列位置。 零優先順序置於功能表列下方的第三個資料列 （列 3） 中的工具列 （資料列 1） 和**標準**工具列 （資料列 2）。 因此，其他工具列會出現在資料列 （優先順序 + 3）。 後續的工具列位於同一個資料列中，如果有足夠的空間。否則，它們會自動移到下一個資料列。  
  
## <a name="default-editor-commands"></a>預設編輯器命令  
 提供自訂編輯器的 VSPackage 應提供預設的工具列，其中包含最重要且經常使用的編輯器中的命令。 當編輯器 為作用中且應該隱藏編輯器 中為非現用時，應該會出現 編輯器 工具列。 此可見性控制的`VisibilityConstraints Element`.vsct 檔。  
  
 編輯器工具列應該有以下 IDE 和 產品 工具列。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
