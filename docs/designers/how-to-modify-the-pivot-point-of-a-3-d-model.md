---
title: "如何：修改 3D 模型的樞紐分析點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：修改 3D 模型的樞紐分析點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文件示範如何使用模型編輯器修改 3D 模型的 *樞紐分析點* 。  樞紐分析點是定義物件的數學中心並旋轉和縮放，處在空間中的點。  
  
 本文件示範此活動:  
  
-   修改物件的樞紐點。  
  
## 修改 3D 模型的樞紐點。  
 您可以透過修改其樞紐點重新定義立體模型的原點。  
  
 確定已顯示 \[**內容**\] 視窗和 \[**工具箱**\]。  
  
#### 修改 3D 模型的樞紐分析點  
  
1.  從現有的立體模型開始，例如 [如何：建立基本 3D 模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)中描述的模型。  
  
2.  進入樞紐分析模式。  在 \[**模型編輯模式**\] 工具列上，選擇 \[**樞紐分析表模式**\] 按鈕以啟動樞紐分析模式。  框在 \[**樞紐分析表模式**\] 按鈕周圍的方塊，表示 \[模型編輯器\] 現在處於樞紐分析模式。  在樞紐模式下，像平移這樣的操作會影響的是物件的樞紐點，而非物件在世界空間中的結構。  
  
3.  修改物件的樞紐點。  在 \[**選取**\] 模式中選取物件，然後在 \[**模型檢視器**\] 工具列上選擇 \[**平移**\] 工具。  表示樞紐分析點的方塊出現在設計介面上。  移動方塊以修改物件的樞紐點。  
  
     您可以移動方塊，在所有三個維度上移動樞紐分析點。  若要沿著一個座標軸平移樞紐點，請移動對應該座標軸的箭號。  方塊和箭號變更成黃色，表示受到轉換影響的座標軸。  
  
     您也可以使用 \[**屬性**\] 視窗中的 \[**樞紐分析表轉譯**\] 屬性指定樞紐分析點。  
  
    > [!TIP]
    >  您旋轉物件以檢視新樞紐分析點的效果。  若要旋轉，請使用 \[**旋轉**\] 工具或修改 \[**旋轉**\] 屬性。  
  
 具有已修改之樞紐點的模型：  
  
 ![具有已修改之樞紐點的房屋模型](~/designers/media/digit-modified-model.png "Digit\-Modified\-Model")  
  
## 請參閱  
 [如何：建立基本 3D 模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [模型編輯器](../designers/model-editor.md)