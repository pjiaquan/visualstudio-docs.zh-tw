---
title: "如何：將著色器套用至 3D 模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：將著色器套用至 3D 模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文件示範如何使用模型編輯器將有向圖形著色器語言 \(DGSL\) 著色器套用至 3D 模型。  
  
 本文件示範此活動:  
  
-   將著色器套用至立體模型  
  
## 將著色器套用至立體模型  
 您可以將著色器效果套用至 3D 模型，使其呈現有趣的外觀。  
  
 開始之前，請先確定已顯示 \[**屬性**\] 視窗。  
  
#### 將著色器套用至 3D 模型  
  
1.  從包含一或多個模型的立體場景開始。  如果您沒有適當的 3\-D 場景，請建立如 [如何：建立基本 3D 模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)中所述。  您也必須具有可套用至模型的 DGSL 著色器。  如果您沒有適當的著色器，請建立如 [如何：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md) 所述並確定您已儲存至檔案，然後才能繼續。  
  
2.  在 \[**選取**\] 模式中，選取模型要將著色器套用至，然後在 \[**屬性**\] 視窗中，於 \[**效果**\] 屬性群組的 \[**filename**\] 屬性，指定要套用至模型的 DGSL 著色器。  
  
 這有基本色彩效果套用至它的模型:  
  
 ![展示基本色彩效果的 3D 場景](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 在您將著色器套用至模型之後，您可以選取模型開啟它在著色器設計工具，然後在 \[**屬性**\] 視窗中，於 \[**效果**\] 屬性群組的 \[**\(進階\)**\] 屬性，選取省略符號 \(\[**...**\]\) 按鈕。  
  
## 請參閱  
 [如何：建立基本 3D 模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [如何：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md)   
 [模型編輯器](../designers/model-editor.md)   
 [著色器設計工具](../designers/shader-designer.md)