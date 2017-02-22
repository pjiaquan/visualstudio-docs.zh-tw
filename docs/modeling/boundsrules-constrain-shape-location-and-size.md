---
title: "BoundsRules 限制圖案位置和大小 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 事件"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
caps.handback.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# BoundsRules 限制圖案位置和大小
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A *範圍規則*是一種類別定義的大小和位置的圖形上的限制。  它提供當使用者拖曳圖形角落或側邊的圖形就會重複呼叫的方法。  
  
 下列範例會限制為帶有子橫條的水平或垂直的固定大小的矩形圖形。  當使用者拖曳角落或側邊時，大綱會翻轉之間允許的兩種組態的高度和寬度。  
  
 範圍規則類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>。  在圖形中建立規則的執行個體：  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 請注意位置和大小可以被限制是否您想要的。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)