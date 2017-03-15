---
title: "字串的項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
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
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>字串的項目
字串的項目必須包含至少一個**ButtonText**子項目。 所有其他子項目是選擇性的。 無效的 XML 字元，例如 'i' 和 '<’ must="" be="" coded="" as="" entities=""></’>&amp;'和'&lt;'，依此類推)。  
  
 連字號文字字串中的指定之命令的鍵盤快速鍵。  
  
## <a name="syntax"></a>語法  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|語言|選擇項。 語言 = 」。 」。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|ButtonText|這個欄位和命令定義五個下列的文字欄位，可讓您指定各種功能表中出現的文字。 根據預設，`ButtonText`欄位會出現在功能表控制器。 `ButtonText`欄位也會成為預設值，如果其他的文字欄位為空白。 `ButtonText`欄位不能空白，即使指定的文字欄位。|  
|工具提示文字|`ToolTipText`欄位指定功能表項目的工具提示中顯示的文字。<br /><br /> 如果`ToolTipText`欄位為空白，`ButtonText`則使用欄位。|  
|MenuText|`MenuText`欄位會指定是否在主功能表中，在快顯功能表中，或在子功能表的工具列，命令會顯示的文字。 如果`MenuText`欄位空白，會使用整合式的開發環境 (IDE)`ButtonText`欄位。 `MenuText`欄位也可以用於當地語系化。<br /><br /> 捷徑功能表，請`MenuText`欄位會顯示在快顯功能表工具列中，啟用自訂在 IDE 中的快顯功能表的名稱。 因此，指明在您命名您的快顯功能表。例如，使用 「 Widget 封裝捷徑功能表 」 而不是 「 捷徑 」。<br /><br /> 如果`MenuText`未指定欄位，`ButtonText`則使用欄位。|  
|CommandName|`CommandName`欄位指定鍵盤類別目錄中所顯示的文字**命令**索引標籤中**自訂**對話方塊 (按一下**自訂**上**工具**功能表)。|  
|CanonicalName|英文`CanonicalName`欄位在英文中可輸入的文字中指定的命令名稱**命令** 視窗中執行的功能表項目。 IDE 會刪除任何不是字母、 數字、 底線或內嵌的句號的字元。 此文字然後串連到`ButtonText`欄位來定義命令。 例如，**新的專案**上**檔案**功能表會變成 File.NewProject 命令。<br /><br /> 如果英文`CanonicalName`未指定欄位時，IDE 會使用`ButtonText` 欄位中，並帶出所有除了字母、 數字、 底線和內嵌的句號。 例如，按鈕文字 「 i 定義命令...」 會變成的 DefineCommands，移除連字號、 空格和省略符號。<br /><br /> 如果`TextChanges`旗標已指定的命令文字會變更，辨識的對應命令**命令**視窗不會變更; 它會保留原始的標準格式`ButtonText`或英文`CanonicalName`欄位。|  
|LocCanonicalName|`LocCanonicalName`欄位作用完全相同的英文`CanonicalName`欄位，但可讓指定當地語系化的命令文字。 您可以指定這兩個標準欄位。 因為 IDE 就會剖析輸入的文字**命令**視窗，並將它與英文和非英文文字的命令可以是相同的命令相關聯。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[Button 元素](../extensibility/button-element.md)|定義使用者可以互動的項目。|  
|[功能表項目](../extensibility/menu-element.md)|定義單一功能表項目。|  
|[下拉式項目](../extensibility/combo-element.md)|定義會出現在下拉式方塊中的命令。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
