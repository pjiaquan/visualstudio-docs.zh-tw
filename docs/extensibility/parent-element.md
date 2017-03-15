---
title: "父項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
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
ms.openlocfilehash: 0da0bd0aceaccdbf8d2cf11fd3490a3e5810ad2e
ms.lasthandoff: 02/22/2017

---
# <a name="parent-element"></a>Parent 項目
按鈕或下拉式方塊的父代可能只是群組。 功能表或群組，可能是功能表或群組的父系。 在[CommandPlacement 元素](../extensibility/commandplacement-element.md)，則需要這個元素，則在所有其他執行個體是選擇性的。 如果省略這個項目，則父代`Group_Undefined:0`會隱含。  
  
## <a name="syntax"></a>語法  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|guid|必要項。 GUID/識別碼 GUID 命令識別項。|  
|id|必要項。 識別碼的 GUID/ID 的命令識別項。|  
  
### <a name="child-elements"></a>子項目  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表命令的 VSPackage 提供整合式的開發環境 (IDE) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
|[按鈕項目](../extensibility/buttons-element.md)|群組[Button 元素](../extensibility/button-element.md)項目。|  
|[功能表項目](../extensibility/menus-element.md)|定義所有 VSPackage 實作的功能表。|  
|[群組項目](../extensibility/groups-element.md)|包含定義的 VSPackage 的命令群組的項目。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
