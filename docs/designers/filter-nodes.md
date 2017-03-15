---
title: "篩選節點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# 篩選節點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在著色器設計工具中，篩選節點會將輸入 \(例如，色彩或材質範例\) 轉換成圖形色彩值。  這些象徵色彩值通常用於產生非相片般真實的效果或其他視覺效果的元素。  
  
## 篩選節點參考  
  
|節點|詳細資料|屬性|  
|--------|----------|--------|  
|**模糊**|使用高斯函數，模糊材質中的像素。<br /><br /> 您可以使用此以在紋理減少色彩詳細資料或雜訊。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 模糊效果的色彩值。|**紋理**<br /> 與模糊期間所用之取樣器產生關聯的材質暫存器。|  
|**反滲透**|減少指定色彩中的色彩量。<br /><br /> 當移除色彩時，色彩值會相當接近灰階。<br /><br /> **輸入：**<br /><br /> `RGB`: `float3`<br /> 反滲透的色彩。<br /><br /> `Percent`: `float`<br /> 要移除的色彩百分比，是用範圍 \[0, 1\]的標準化值來表示。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 去飽和色彩。|**明亮度**<br /> 提供給紅色、綠色和藍色色彩元件的加權。|  
|**邊緣偵測**|使用 Canny 邊緣偵測器偵測到材質中的邊緣。  邊緣像素輸出為白色，非邊緣像素輸出為黑色。<br /><br /> 您可以用這個來識別材質中的邊緣，以便使用其他效果來處理邊緣像素。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 如果 texel 在邊緣則為白色；否則為黑色。|**紋理**<br /> 與邊緣偵測期間所用之取樣器產生關聯的材質暫存器。|  
|**銳利化**|銳利化材質。<br /><br /> 您可以使用此以加亮顯示紋理的細微的詳細資料。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 模糊效果的色彩值。|**紋理**<br /> 與銳利化期間所用之取樣器產生關聯的材質暫存器。|