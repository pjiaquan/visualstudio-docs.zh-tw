---
title: "延伸標記 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.span"
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 延伸標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

延伸標記表示應用程式有意義的階段。  例如，您可以使用延伸區塊來標示在執行的特定工作項目處理的時間間隔。  其長度表示對應的應用程式階段的期間。  以下會顯示一個並行視覺化檢視的延伸區塊:  
  
 ![&#91;並行視覺化檢視&#93; 中的延伸標記](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
並行視覺化檢視中的延伸標記  
  
## 延伸類別  
 延伸標記根據其分類以五個不同的色彩來顯示。  如果超過五種類別，色彩將重複使用。  類別可以是任何整數。  下圖顯示五個可能色彩:  
  
 ![五個不同分類的延伸標記](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
前五個延伸類別的色彩  
  
## 彙總資料標記延伸  
 有時後若候延伸標記發生，請關閉"並行視覺化檢視"，因為其無法個別繪製。  發生這種情況時，基礎延伸的灰色 *延伸彙總資料標記*會顯示。  當您的滑鼠停留在這些圖示的其中一個上面，工具提示會顯示表示基礎延伸的數目。  若要檢視間距，請將其放大。  如果您一直放大和但是仍只取得延伸彙總資料標記，您可以查看 [標記報告](../profiling/markers-report.md)中的基礎延伸標記。  下圖顯示一個延伸彙總資料標記:  
  
 ![&#91;並行視覺化檢視&#93; 中的彙總延伸標記](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
彙總資料標記延伸  
  
## 請參閱  
 [並行視覺化檢視中的標記](../profiling/concurrency-visualizer-markers.md)   
 [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)