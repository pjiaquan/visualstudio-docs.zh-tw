---
title: "命令位置指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
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
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>命令位置指導方針
最佳作法在 Visual Studio 整合式的開發環境 (IDE) 中放置命令的命令集的大小而異。 定義命令和定位根據.vsct 檔案中的資訊。  
  
## <a name="best-practices-for-all-command-sets"></a>所有的命令集的最佳作法  
 每一組命令，請遵循下列準則︰  
  
-   事先準備命令結構的圖表。 識別命令、 下拉式方塊中，命令群組和使用於多個位置的捷徑功能表。  
  
-   應該與顯示在相同群組中的命令。  
  
-   群組包含一個命令是可接受的。  
  
-   封裝應該新增至現有的 Visual Studio 功能表的許多命令。 相反地，他們應該建立功能表或子功能表來裝載新的命令。  
  
-   當您將指令上現有的功能表命令的名稱，讓它的目的是清除並不會混淆與現有的命令。  
  
## <a name="best-practices-for-small-command-sets"></a>小型的命令集的最佳作法  
 如果您正在開發具有幾個命令的 VSPackage，也請遵循這些指導方針︰  
  
-   可能的話，請使用[父項目](../../extensibility/parent-element.md)的命令、 下拉式方塊、 群組或子功能表將它放在適當的群組。  
  
-   將這些群組指派到 VSPackage 所顯示的功能表。  
  
-   子功能表或命令的父系必須是[群組項目](../../extensibility/group-element.md)。 指派給群組，命令和子功能表，然後將群組指派給父功能表。  
  
-   您可以藉由新增額外的群組中將指令[CommandPlacements 元素](../../extensibility/commandplacements-element.md)區段之後定義的命令，然後再將加入`CommandPlacements Element` [CommandPlacement 元素](../../extensibility/commandplacement-element.md)針對每個額外的群組。  
  
## <a name="best-practices-for-large-command-sets"></a>較大的命令集的最佳作法  
 VSPackage 有許多命令將會出現在多個內容，也請遵循這些指導方針︰  
  
-   請在功能表、 群組和自我的父代的命令。 也就是說，請勿指派`Parent Element`定義中的項目。  
  
-   使用`CommandPlacement Element`中的項目`CommandPlacements Element`一節，以將功能表、 群組和命令放在其父功能表和群組。  
  
-   在`CommandPlacements`區段中，填入指定的功能表項目或群組應在彼此相鄰。 這有助於提高可讀性，並使`Priority`排名容易判定。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令資料表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
