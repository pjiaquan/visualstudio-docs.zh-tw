---
title: "XMLNode 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLNode 控制項"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode 控制項
  在**重要** 有關 Microsoft Word 的本主題開頭的資訊位於美國境外及其疆土或者使用對個人的優點和使用完整呈現和組織，或者執行中開發程式，由在選取範圍從之前的 Microsoft 授權之 Microsoft Word 產品，，當 Microsoft 從 Microsoft Word 移除特定功能的實作與自訂 XML 相關。  這些有關 Microsoft Word 的資訊不得供位於美國或其行政區以內，使用 Microsoft 在 2010 年 1 月 10 日以後所授權之 Microsoft Word 產品或開發適用程式之個人或組織閱讀或使用。凡是在該日期以前授權或是針對在美國地區以外使用所購買並授權的這些產品，其行為將有所不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項是一個對應 XML 節點物件，會公開事件，且可以繫結至資料。  只有當有不重複的結構描述項目對應至 Microsoft Office Word 文件時，才會建立 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。  在 Visual Studio 建立 XML 節點之後，您可以直接對其進行程式設計，而不必周遊 Word 物件模型。  
  
 只有移除 Word 中的項目對應，才能刪除 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。  
  
## 將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項支援簡單的資料繫結 \(Data Binding\)。  XML 節點應該透過 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 屬性繫結至資料來源。  如果繫結資料集中的資料受到更新，<xref:Microsoft.Office.Tools.Word.XMLNode> 控制項就會反映這些變更。  
  
## 格式  
 可套用至 <xref:Microsoft.Office.Interop.Word.XMLNode> 物件的格式同樣可以套用至 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。  這包括字型、底線樣式以及字元樣式。  
  
## 事件  
 下列事件適用於 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## 比較事件  
 您可以在使用者於特定 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項內容中移動游標時擷取事件。  例如，您可能有名為 `Customer` 的 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項，該控制項有名為 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNode> 子控制項，而 `Company` 有名為 `CompanyName` 和 `CompanyRegion` 的兩個 <xref:Microsoft.Office.Tools.Word.XMLNode> 子控制項，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果每當游標移至 `Company` 節點內，您就要在執行窗格上顯示控制項，則游標是否放在 `CompanyName` 或 `CompanyRegion` 中都應該無關，因為這兩者都是在 `Company` 的內容中。  此時，您可以在 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件中撰寫程式碼。  
  
 在大部分情況下，當游標進入 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項時，會同時引發 <xref:Microsoft.Office.Tools.Word.XMLNode.Select> 和 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件，  下表顯示這些事件之間的差異。  
  
|Select 事件|ContextEnter 事件|  
|---------------|---------------------|  
|當游標放入 <xref:Microsoft.Office.Tools.Word.XMLNode> 時發生。|當游標從節點內容以外的區域，放到 <xref:Microsoft.Office.Tools.Word.XMLNode> 或其中一個子代節點時發生。  也就是說，它只會在內容變更時引發。|  
  
 例如，當您將游標從 `Customer` 外部移至 `CompanyName` 內時，會引發 `Customer`、`Company` 和 `CompanyName` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件。  如果您接著將游標從 `CompanyName` 移到 `CompanyRegion`，則只會引發 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件，因為游標還在 `Company` 和 `Customer` 的內容中。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> 事件和 <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> 事件之間也存在相同的差異。  
  
## 請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes 控制項](../vsto/xmlnodes-control.md)   
 [如何：將 XMLNode 控制項加入至 Word 文件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何：在 Visual Studio 內將結構描述對應至 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  