---
title: "自訂項目工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# 自訂項目工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在一些 DSL 定義中，您一組項目代表單一的概念。 比方說，如果您建立的模型元件都具有一組固定的通訊埠，您一定想在其父元件在同一時間建立的連接埠。 因此，您必須自訂的項目建立工具，因此它會建立一組項目，而不是其中一個。 若要達到此目的，您可以自訂如何初始化的項目建立工具。  
  
 您也可以覆寫此工具拖曳到圖表或項目時，會發生什麼事。  
  
## 自訂項目工具的內容  
 每個項目工具會將儲存的執行個體 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\)，其中包含一或多個模型項目和連結的序列化的版本。 根據預設，項目工具 EGP 包含一個類別，以您指定工具的執行個體。 您可以藉由覆寫變更此 *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`。 載入 DSL 封裝時，會呼叫這個方法。  
  
 方法的參數是類別的您在 DSL 定義中指定 ID。 您感興趣的類別呼叫方法時，您可以加入額外的項目到 EGP。  
  
 EGP 必須包含內嵌至附屬項目從一個主要的項目連結。 它也可以包含參考連結。  
  
 下列範例會建立主要的項目和兩個內嵌的項目。 主要的類別稱為反對，而且具有名為 「 終端機項目的兩個內嵌關聯性。 Terminal1 和 Terminal2，命名內嵌角色內容，且兩者都有多重性為 1..1。  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## 請參閱  
 [自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)