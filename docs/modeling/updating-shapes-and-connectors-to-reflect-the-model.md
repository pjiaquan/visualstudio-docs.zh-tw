---
title: "更新圖案和接點來反映模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>更新圖案和接點來反映模型
以網域特定語言中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您可以進行反映基礎模型的狀態圖形的外觀。  
  
 本主題中的程式碼範例應加入至`.cs`檔案位於您`Dsl`專案。 您必須在每個檔案的這些陳述式︰  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>設定圖案對應的屬性，來控制 decorator 的可視性  
 您可以控制 decorator 的可視性，而不需要撰寫程式碼中，藉由設定 DSL 定義中的圖形和網域類別之間的對應。 如需詳細資訊，請參閱 [如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)。
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>將公開為屬性的色彩和樣式的圖形  
 在 DSL 定義中，以滑鼠右鍵按一下圖形類別，並指向**加入已公開**，然後按一下其中一個項目例如**填滿色彩**。  
  
 圖形現在具有您可以設定在程式碼或使用者的網域屬性。 例如，要將它設定的命令或規則的程式碼中，您可以撰寫︰  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 如果您想要將屬性的變數只在程式控制下而不是由使用者，選取新的網域屬性例如**填滿色彩**DSL 定義圖表中。 然後，在 [屬性] 視窗中，將**是可瀏覽**至`false`或設定**是 UI Readonly**到`true`。  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定義變更規則，使色彩、 樣式或位置取決於模型項目屬性  
 您可以定義規則，更新相依於模型的其他部分圖形的外觀。 例如，您可以定義變更規則更新相依內容的模型項目及其圖案的色彩模型項目上。 如需有關變更規則的詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 您只能更新存放區中，內進行維護的屬性，因為規則不會叫用 [復原] 命令會在執行時應該使用規則。 這不包括一些圖形化的功能，例如大小和形狀的可見性。 若要更新圖形的功能，請參閱[更新非存放區圖形功能](#OnAssociatedProperty)。  
  
 下列範例假設您有公開`FillColor`為上一節中所述的網域屬性。  
  
```c#  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>使用 OnChildConfigured 初始化圖形的屬性  
 若要設定圖形的屬性，第一次時，建立覆寫`OnChildConfigured()`部分圖表類別定義中。 在 DSL 定義中，指定圖表的類別，而產生的程式碼位於**Dsl\Generated Code\Diagram.cs**。 例如:   
  
```c#  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 這個方法可以用於網域內容和非存放區功能，例如圖形的大小。  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>若要更新圖形的其他功能使用 AssociateValueWith()  
 某些功能的圖形，例如是否具有陰影或連接器的箭頭樣式沒有內建方法公開為網域屬性的功能。  這類功能的變更不是在交易系統的控制之下。 因此，不適合用於更新這些使用規則，因為規則不會叫用使用者執行 [復原] 命令時。  
  
 相反地，您可以使用<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>更新等功能 在下列範例中，連接器的箭頭樣式會受到此連接器會顯示關聯性中的定義域屬性的值︰  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape’s built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`應該會呼叫一次針對每個您想要註冊的網域屬性。 已呼叫之後，會呼叫指定之屬性的任何變更`OnAssociatedPropertyChanged()`中呈現屬性的模型項目中的任何圖形。  
  
 不需要呼叫`AssociateValueWith()`每個執行個體。 雖然 InitializeResources 執行個體方法，它會叫用一次只能針對每個圖形類別。

