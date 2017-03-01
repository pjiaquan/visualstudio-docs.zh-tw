---
title: "UsedCommands 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 13
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
ms.openlocfilehash: 2988cc106a87f82dc2a670076e9ff396802b7644
ms.lasthandoff: 02/22/2017

---
# <a name="usedcommands-element"></a>UsedCommands 項目
UsedCommands 項目群組 UsedCommand 項目和其他 UsedCommands 群組。  
  
 UsedCommands 項目是選擇性的。 如果您不會呼叫您的封裝外部所定義的命令，您就不需要包括.vsct 檔案中的這一節。  
  
## <a name="syntax"></a>語法  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇項。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[UsedCommand 項目](../extensibility/usedcommand-element.md)|由其他程式碼所實作的命令。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表 VSPackage 所提供的命令 （例如，功能表項目、 功能表、 工具列和下拉式方塊），整合式的開發環境 (IDE) 的所有項目。|  
  
## <a name="example"></a>範例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [UsedCommand 項目](../extensibility/usedcommand-element.md)   
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
