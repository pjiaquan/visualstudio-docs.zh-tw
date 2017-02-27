---
title: "使用者的意見反應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用者模型意見"
  - "環境、 內容"
  - "IDE、 內容"
  - "IDE 中，使用者意見反應"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用者的意見反應
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)、 有關可用的功能以使用者目前的選取項目和全域的選取範圍內容為基礎的視覺化回應。  下表列出不同的選取項目內容中所提供的功能。  
  
|選取範圍內容|可用的功能|  
|------------|-----------|  
|IDE|Global|  
|目前的產品集合|特定的產品|  
|使用中的階層架構|階層架構型別特定|  
|使用中的階層架構項目|階層架構項目型別特定|  
|使用中的文件|特定文件類型|  
|最上層的多重文件介面 \(MDI\) 視窗|視窗型別特定|  
|目前的選取範圍內容|特定的選取範圍內容|  
  
 如果您只會出現使用者需要與持續提供一致的選取範圍和環境內容的意見反應的功能，則會減少在 IDE 中的複雜性。  在 IDE 中開啟的視窗時，就會套用下列規則：  
  
-   如果視窗中變更它的選取範圍內文，選取回應清楚說明在視窗\]，然後動態說明\] 視窗中，如果顯示，會更新以反映目前的內容。  
  
-   如果視窗是全域的選取項目內容的變更，所有的特定內容的功能表、 \[作用中的階層架構\] 視窗中和應用程式的標題列會更新以反映目前的內容。  
  
-   視窗應該出現在目前的選取項目的內容**屬性** 視窗也可選擇性地顯示，如果 **屬性頁**對話方塊。  
  
-   如果視窗不會出現屬性或變更全域的選取範圍內容，選取回應視窗中不應該會維持，不再在 IDE 中的使用中視窗時。  
  
-   所有的特定文件的工具視窗持續應反映出使用中的文件。  
  
-   功能表、 工具列及應用程式的標題列應反映出最上層的多重文件介面 \(MDI\) 的 \[用戶端\] 視窗。  
  
 例如，Web Form 專案內的 Visual Basic 的 Web 應用程式的 \[HTML\] 檢視會開啟，並在使用者選取`<td>`標記，以下列方式提供意見反應：  
  
-   選取項目是使用中視窗所示，反映在**屬性**視窗。  
  
-   特定文件**工具箱**會更新以反映目前的文件。  
  
-   **編輯器** 工具列和 **資料表**功能表會顯示和更新以反映 Web Form 視窗的標題列。  
  
-   使用中的階層視窗中，通常是**方案總管\] 中**，以及它的標題列更新程式，以反映目前的內容和即時線上 **專案**功能表命令現在可套用至作用中的 Web 應用程式專案。  
  
## 請參閱  
 [選取項目和 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)   
 [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)