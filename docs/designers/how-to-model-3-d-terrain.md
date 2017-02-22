---
title: "如何：為 3D 地形建立模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
caps.handback.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 如何：為 3D 地形建立模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文件示範如何使用模型編輯器建立 3D 地形模型。  
  
 本文件示範下列活動:  
  
-   將物件加入至場景  
  
-   選取表面和點  
  
-   轉譯選項  
  
-   使用 \[**細分表面**\] 工具  
  
-   在設計介面上框限物件  
  
## 建立立體地形模型  
 您可以將平面細分成其他表面，然後操作其端點來製作有趣的地形特性，以建立 3D 地形。  
  
 當您完成時，模型看起來應該像這樣：  
  
 ![顯示地形模型的 3D 場景](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 開始之前，請先確定已顯示 \[**屬性**\] 視窗和 \[**工具箱**\]。  
  
#### 建立 3D 地形模型  
  
1.  建立 3\-D 模型使用。  如需有關如何將模型加入至專案的詳細資訊，請參閱[模型編輯器](../designers/model-editor.md)中的＜使用者入門＞一節。  
  
2.  將平面加入至場景。  在 \[**圖形**\] 下的 \[**工具箱**\] 中，選取 \[**平面**\] 並將其移至設計介面。  
  
    > [!TIP]
    >  要讓平面物件更容易處理，可以在設計介面中加上框架。  在 \[**選取**\] 模式中選取平面物件，然後在模型編輯工具列上選擇 \[**框架物件**\] 按鈕。  
  
3.  進入表面選取模式。  在模型編輯器工具列上，選擇 \[**選取表面**\]。  
  
4.  將平面分成子區塊。  在表面選取模式下，選取平面一次以啟動它做選取，然後再選取一次選取其唯一的表面。  在模型編輯器工具列上，選擇 \[**細分表面**\]。  這會將新端點加入至分割為四個平均分割大小的平面。  
  
5.  建立更多細分。  保持新面孔仍被選取，請再選擇 \[**細分表面**\] 兩次。  這樣總共會建立 64 種卡面。  藉由建立更多細分，您可以提供這個地形更詳細資料。  
  
6.  進入點選取模式。  在模型編輯器工具列上，選擇 \[**選取點**\]。  
  
7.  修改一點以建立地形功能。  在點選取模式中，選取其中一個點，然後在模型編輯工具列上選擇 \[**平移**\] 工具。  表示該點的方塊出現在設計介面上。  使用綠色箭號移動方塊，從而修改點的高度。  針對不同點重複這個步驟，以建立有趣的地形功能。  
  
    > [!TIP]
    >  您可以一次選取多個點並統一修改。  
  
 地形模型已完成。  以下為最終模型，套用 Phong 著色法:  
  
 ![顯示地形模型的 3D 場景](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 您可以使用這個地形模型展示 [如何：建立以幾何為基礎的漸層著色器](../designers/how-to-create-a-geometry-based-gradient-shader.md)中描述的漸層著色器效果。  
  
## 請參閱  
 [模型編輯器](../designers/model-editor.md)