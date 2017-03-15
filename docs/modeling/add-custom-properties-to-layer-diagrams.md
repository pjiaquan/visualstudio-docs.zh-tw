---
title: "將自訂屬性加入至相依性圖表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 21
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 6c7e43c180ac5210d9c29961ed7330b370a99075
ms.lasthandoff: 02/22/2017

---
# <a name="add-custom-properties-to-dependency-diagrams"></a>將自訂屬性加入至相依性圖表
當您撰寫相依性圖表的延伸模組程式碼時，您可以在相依性圖表上儲存任何項目的值。 當分層圖儲存並重新開啟時，值會保存下來。 您也可以讓這些屬性會出現在**屬性**視窗，讓使用者可以看到並加以編輯。 例如，您可以讓使用者為每個圖層指定規則運算式，並且撰寫驗證程式碼驗證每個圖層中類別的名稱符合使用者指定的模式。  
  
## <a name="properties-not-visible-to-the-user"></a>使用者看不見的屬性  
 如果您只想將值附加至相依性圖表中的任何元素的程式碼，您不需要定義 MEF 元件。 沒有名為字典`Properties` <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>。</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> 只要將可封送處理的值加入至任何圖層項目的字典中即可。 這些值會儲存為相依性圖表的一部分。 如需詳細資訊，請參閱[巡覽和更新圖層的程式碼中的模型](../modeling/navigate-and-update-layer-models-in-program-code.md)。  
  
## <a name="properties-that-the-user-can-edit"></a>使用者可以編輯的屬性  
 **初始準備工作**  
  
> [!IMPORTANT]
>  若要讓屬性出現，您必須在要讓圖層屬性顯示的每部電腦上執行下列變更。  
>   
>  1.  使用 [記事本] 來執行**系統管理員身分執行**。 開啟 `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`  
> 2.  在 `Content` 項目內，加入：  
>   
>     ```xml  
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>     ```  
> 3.  在**Visual Studio Tools**區段的 [Visual Studio 應用程式開始] 功能表，開啟**開發人員命令提示字元**。  
>   
>      輸入：  
>   
>      `devenv /rootSuffix /updateConfiguration`  
>   
>      `devenv /rootSuffix Exp /updateConfiguration`  
> 4.  重新啟動 Visual Studio。  
  
 **請確定您的程式碼位於 VSIX 專案**  
  
 如果您的屬性是命令、筆勢或驗證專案的一部分，則不需要加入任何項目。 自訂屬性的程式碼應該在定義為 MEF 元件的 Visual Studio 擴充性專案中定義。 如需詳細資訊，請參閱[相依性圖表中加入命令和軌跡](../modeling/add-commands-and-gestures-to-layer-diagrams.md)或[相依性圖表中加入自訂架構驗證](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)。  
  
 **定義自訂屬性**  
  
 若要建立自訂屬性，請依照下述定義類別：  
  
```  
[Export(typeof(IPropertyExtension))]  
public class MyProperty   
      : PropertyExtension<ILayerElement>  
{  
  // Implement the interface.  
}  
```  
  
 您可以在定義屬性<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>或任何其衍生的類別，其中包括︰</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>  
  
-   `ILayerModel` - 模型  
  
-   `ILayer` - 每個圖層  
  
-   `ILayerDependencyLink` - 圖層之間的連結  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
## <a name="example"></a>範例  
 下列程式碼是典型自訂屬性描述元。 它會在圖層模型上定義布林值屬性 (`ILayerModel`)，而圖層模型可讓使用者提供自訂驗證方法的值。  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
  
namespace MyNamespace  
{  
  /// <summary>  
  /// Custom properties are added to the Layer Designer via a custom  
  /// Property Descriptor. We have to export this Property Descriptor  
  /// using MEF to make it available in the Layer Designer.  
  /// </summary>  
  [Export(typeof(IPropertyExtension))]  
  public class AllTypesMustBeReferencedProperty   
      : PropertyExtension<ILayerModel>  
  {  
    /// <summary>  
    /// Each custom property must have a unique name.   
    /// Usually we use the full name of this class.  
    /// </summary>  
    public static readonly string FullName =  
      typeof(AllTypesMustBeReferencedProperty).FullName;  
  
    /// <summary>  
    /// Construct the property. Notice the use of FullName.  
    /// </summary>  
    public AllTypesMustBeReferencedProperty()  
            : base(FullName)  
    {  }  
  
    /// <summary>  
    /// The display name is shown in the Properties window.  
    /// We therefore use a localizable resource.  
    /// </summary>  
    public override string DisplayName  
    {  
      get { return Strings.AllTypesMustBeReferencedDisplayName; }  
    }  
  
    /// <summary>  
    /// Description shown at the bottom of the Properties window.  
    /// We use a resource string for easier localization.  
    /// </summary>  
    public override string Description  
    {  
      get { return Strings.AllTypesMustBeReferencedDescription; }  
    }  
  
    /// <summary>  
    /// This is called to set a new value for this property. We must  
    /// throw an exception if the value is invalid.  
    /// </summary>  
    /// <param name="component">The target ILayerElement</param>  
    /// <param name="value">The new value</param>  
    public override void SetValue(object component, object value)  
    {  
      ValidateValue(value);  
      base.SetValue(component, value);  
    }  
    /// <summary>  
    /// Helper to validate the value.  
    /// </summary>  
    /// <param name="value">The value to validate</param>  
    private static void ValidateValue(object value)  
    {  }  
  
    public override Type PropertyType  
    { get { return typeof(bool); } }  
  
    /// <summary>  
    /// The segment label of the properties window.  
    /// </summary>  
    public override string Category  
    {   
      get  
      {  
        return Strings.AllTypesMustBeReferencedCategory;  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充相依性圖表](../modeling/extend-layer-diagrams.md)

