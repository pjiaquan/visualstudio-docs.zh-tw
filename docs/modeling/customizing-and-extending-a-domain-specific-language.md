---
title: "自訂及擴充定義域專屬語言 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>自訂及擴充網域指定的語言
Visual Studio 模型和視覺效果 SDK (VMSDK) 提供數個層級定義模型工具︰  
  
1.  定義使用 DSL 定義圖表的定義域專屬語言 (DSL)。 您可以使用圖表標記法，可讀取的 XML 格式，並產生程式碼和其他成品所需的基本工具，快速建立 DSL。  
  
     如需詳細資訊，請參閱[如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)。  
  
2.  使用 DSL 定義的更進階的功能來微調 DSL。 例如，您可以進行其他使用者建立的項目時顯示的連結。 這些技術大多可在 DSL 定義中，而某些需要幾行程式碼。  
  
3.  使用程式碼來擴充模型化工具。 VMSDK 是為了能讓您輕鬆整合擴充功能與從 DSL 定義產生的程式碼而專門設計的。  如需詳細資訊，請參閱[用來自訂網域特定語言撰寫程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。  
  
> [!NOTE]
>  當您已更新的 DSL 定義檔時，別忘了按一下**轉換所有範本**後再重建您的方案的 [方案總管] 工具列中。  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>本章節內容  
  
|若要達成這個效果|請參閱本主題|  
|----------------------------|-------------------------|  
|允許使用者設定圖形的色彩和樣式屬性。|以滑鼠右鍵按一下圖形或連接器類別，並指向**加入已公開**，按一下項目。<br /><br /> 請參閱[自訂圖表上的展示](../modeling/customizing-presentation-on-the-diagram.md)。|  
|不同類別的模型項目類似在圖表中，共用屬性，例如初始高度和寬度、 色彩、 工具提示。|使用圖形或連接器類別之間的繼承。 在衍生的圖形與衍生的網域類別之間的對應繼承父系的對應詳細資料。<br /><br /> 或者，您也可以將不同的網域類別對應至相同的圖形類別。|  
|類別的模型項目會顯示不同的圖形內容。|將多個圖形類別對應至相同的網域類別。 當您建置方案時，請遵循錯誤報告，並提供要求的程式碼，以決定要使用何種圖形。|  
|圖形色彩或字型等其他功能會指出目前的狀態。|請參閱[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 建立更新公開的屬性的規則。 請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，使用 OnAssociatedPropertyChanged() 更新非公開的功能，例如連結箭號或字型。|  
|指出狀態的變更圖形上的圖示。|在 [DSL 詳細資料] 視窗設定裝飾項目對應的可見性。 找出相同的位置上的數個映像裝飾項目。 請參閱[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或者，您也可以覆寫`ImageField.GetDisplayImage()`。 請參閱<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>範例|  
|設定在圖形的背景影像|若要新增錨定的 ImageField InitializeInstanceResources() 會覆寫。 請參閱[自訂圖表上的展示](../modeling/customizing-presentation-on-the-diagram.md)。|  
|任意深度的巢狀處理圖案|設定內嵌樹狀目錄中的遞迴。 定義包含圖形 BoundsRules。 請參閱[自訂圖表上的展示](../modeling/customizing-presentation-on-the-diagram.md)。|  
|附加在固定的點上的項目界限的連接器。|定義內嵌的終端機項目，由小圖表上的連接埠。 若要修正之連接埠就地使用 BoundsRules。 電路圖表範例，請參閱[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)。|  
|文字欄位會顯示衍生自其他值的值。|將文字裝飾項目對應至計算或自訂儲存網域屬性。 如需詳細資訊，請參閱[計算和儲存體的自訂內容](../modeling/calculated-and-custom-storage-properties.md)。|  
|將模型項目，或圖形之間的變更傳播|請參閱[驗證定義域專屬語言](../modeling/validation-in-a-domain-specific-language.md)。|  
|將變更傳播至資源，例如其他[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]外部存放區的延伸模組。|請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|  
|屬性視窗會顯示相關項目的屬性。|設定轉送屬性。 請參閱[自訂屬性 視窗](../modeling/customizing-the-properties-window.md)。|  
|屬性類別|[屬性] 視窗分為稱 [分類] 的區段。 設定**類別**的網域屬性。 屬性具有相同的類別目錄名稱會出現在相同的區段。 您也可以設定**類別**的關聯性角色。|  
|網域內容控制使用者存取|設定**是可瀏覽**false，以防止網域屬性在執行階段出現在 [屬性] 視窗中。 您仍然可以將它對應至文字裝飾項目。<br /><br /> **是 UI Read Only**防止使用者變更網域屬性。<br /><br /> 不會影響到網域屬性的程式存取。|  
|變更名稱、 圖示和可見性，您的 DSL 模型總管 中的節點。|請參閱[自訂模型總管](../modeling/customizing-the-model-explorer.md)。|  
|啟用複製、 剪下和貼上|設定**啟用複製貼上**屬性**編輯器**DSL 總管 中的節點。|  
|複製參考連結並複製項目是每當其目標。 例如，將複製的項目附加註解。|設定**傳播複本**來源角色 （由 DSL 定義圖表中的網域關聯性的一端上的行） 的屬性。<br /><br /> 撰寫程式碼來覆寫 ProcessOnCopy 以取得更複雜的效果。<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|刪除、 重設父代，或刪除項目時，重新連結相關項目。|設定**傳播刪除**關聯性角色的值。 針對更複雜的效果，覆寫`ShouldVisitRelationship`和`ShouldVisitRolePlayer`方法`MyDslDeleteClosure`中定義的類別**DomainModel.cs**<br /><br /> 請參閱[自訂刪除行為](../modeling/customizing-deletion-behavior.md)|  
|保留圖形版面配置和外觀上複製和拖放。|將圖形和連接線加入至複製`ElementGroupPrototype`。 若要覆寫最方便的方法是`ElementOperations.CreateElementGroupPrototype()`<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|在選擇的位置貼上圖形，例如目前的游標位置。|覆寫`ClipboardCommandSet.ProcessOnCopy()`若要使用的特定位置版本`ElementOperations.Merge().`看到[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|貼上建立其他連結|覆寫 ClipboardCommandSet.ProcessOnPasteCommand()|  
|啟用從拖放此圖中，其他 Dsl 和 Windows 項目|請參閱[How to︰ 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|讓圖形或工具將它們拖曳至 「 子 」 圖形，例如連接埠，如同它已拖曳至父代。|定義目標物件類別，來卸除的物件轉送給父項目合併指示詞。 請參閱[自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|  
|讓圖形或將它們拖曳至圖形，並讓其他連結的工具或建立的物件。 例如，若要允許註解可以放到它為連結的項目。|項目合併指示詞上定義目標網域類別，並定義要產生連結。 在複雜的情況下，您可以加入自訂程式碼。 請參閱[自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|  
|使用其中一個工具，建立一組項目。 例如，具有一組固定的通訊埠的元件。|覆寫 ToolboxHelper.cs 中的工具箱初始化方法。 建立項目群組原型 (EGP) 包含的項目和其關聯性連結。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 請在 EGP 中包含主體和連接埠圖形，或定義 BoundsRules EGP 具現化時通訊埠圖案的位置。 請參閱[BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)。|  
|使用一個連接工具來具現化的幾種類型的關聯性。|將連結連線指示詞 (LCD) 加入至連接產生器所叫用的工具。 Lcd 判斷兩個項目類型的關聯性的類型。 若要使這項目的狀態而定，您可以加入自訂程式碼。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|  
|自黏工具 – 使用者可以按兩下任何工具來建立連續的許多圖形或連接器。|在 DSL 總管 中，選取 `Editor`節點。 在 [屬性] 視窗中，設定**使用列在首位的工具箱項目**。|  
|定義功能表命令|請參閱[如何︰ 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|限制與驗證規則的模型|請參閱[定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)|  
|從 DSL 中產生程式碼、 組態檔或文件。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|  
|自訂如何儲存模型檔案。|請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|將模型儲存至資料庫或其他媒體。|覆寫*YourLanguage*DocData<br /><br /> 請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|將數個 Dsl 整合，讓它們能夠做為一個應用程式的一部分。|請參閱[整合的模型，使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|  
|允許協力廠商擴充 DSL 和控制擴充功能。|[使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 程式庫共用 DSL 之間的類別](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>另請參閱  
 [如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [撰寫程式碼來自訂定義域專屬語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


