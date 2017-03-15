---
title: "如何：使用 WPF 樹狀架構視覺化檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯, WPF"
  - "WPF, 偵錯"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用 WPF 樹狀架構視覺化檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 \[WPF 樹狀架構視覺化檢視\] 瀏覽 WPF 物件的視覺化樹狀結構，以及檢視該樹狀結構內含物件的 WPF 相依性屬性。  如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../Topic/Trees%20in%20WPF.md)。  如需相依性屬性的詳細資訊，請參閱[相依性屬性概觀](../Topic/Dependency%20Properties%20Overview.md)。  
  
 當您開啟 \[WPF 樹狀結構視覺化檢視\] 時，會看見兩個窗格：左側的 \[**視覺化樹狀結構**\] 和右側的 \[*Name* 的**屬性:***Type*\] 窗格。  只要在 \[**視覺化樹狀結構**\] 窗格中選取任何物件，\[*Name* 的**屬性:***Type*\] 窗格就會自動更新以顯示該物件的屬性。  
  
### 若要開啟 WPF 樹狀架構視覺化檢視  
  
1.  在 DataTip \[**監看式**\] 視窗、\[**自動變數**\] 視窗或 \[**區域變數**\] 視窗中，在 WPF 物件名稱旁，按一下放大鏡圖示旁邊的箭號。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下 \[**WPF 樹狀架構視覺化檢視**\]。  
  
### 若要搜尋視覺化樹狀結構  
  
-   在 \[**視覺化樹狀結構**\] 窗格的 \[**搜尋**\] 方塊中，輸入要搜尋的字串。  
  
     \[WPF 樹狀架構視覺化檢視\] 會立即在視覺化樹狀結構中，尋找第一個符合您輸入之字串的物件。  輸入越多字元，尋找的相符項目越精確。  
  
    -   若要移至視覺化樹狀結構中的下一個相符項目，請按 \[**下一個**\]。  
  
    -   若要移至上一個符合項目，則按一下 \[**上一個**\]。  
  
    -   若要清除搜尋準則，請按一下 \[**清除**\]。  
  
### 若要搜尋屬性清單  
  
-   在 \[*Name* 的**屬性:***Type*\] 窗格的 \[**篩選**\] 方塊中，輸入要搜尋的字串。  
  
     \[WPF 樹狀架構視覺化檢視\] 會立即尋找符合您輸入之字串的屬性；現在，清單只會顯示符合您所輸入字串的屬性。  輸入越多字元，尋找的相符項目越精確。  
  
    -   若要清除搜尋準則，請按一下 \[**清除**\]。  
  
### 若要關閉視覺化檢視  
  
-   按一下對話方塊右上角中的 \[**關閉**\] 圖示。  
  
## 請參閱  
 [如何：使用視覺化檢視](../Topic/How%20to:%20Use%20a%20Visualizer.md)   
 [視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [WPF 中的樹狀結構](../Topic/Trees%20in%20WPF.md)   
 [相依性屬性概觀](../Topic/Dependency%20Properties%20Overview.md)