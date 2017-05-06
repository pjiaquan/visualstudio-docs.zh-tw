---
title: "XMLNodes 控制項"
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
  - "XMLNodes 控制項"
  - "XMLNodes 控制項, 事件"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes 控制項
  在**重要** 有關 Microsoft Word 的本主題開頭的資訊位於美國境外及其疆土或者使用對個人的優點和使用完整呈現和組織，或者執行中開發程式，由在選取範圍從之前的 Microsoft 授權之 Microsoft Word 產品，，當 Microsoft 從 Microsoft Word 移除特定功能的實作與自訂 XML 相關。  這些有關 Microsoft Word 的資訊不得供位於美國或其行政區以內，使用 Microsoft 在 2010 年 1 月 10 日以後所授權之 Microsoft Word 產品或開發適用程式之個人或組織閱讀或使用。凡是在該日期以前授權或是針對在美國地區以外使用所購買並授權的這些產品，其行為將有所不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項是公開 \(Expose\) 事件的對應 XML 節點物件集合。  只有當重複的結構描述項目對應至 Microsoft Office Word 文件時，才會建立 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。  如果重複的項目包含子項目，則每個子項目也會建立為 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。  
  
 Visual Studio 建立 XML 節點的集合之後，您就可以直接對控制項進行程式設計，而不必周遊 Word 物件模型。  只有移除文件中的項目對應，才能刪除 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。  
  
> [!NOTE]  
>  如果透過 <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> 屬性存取 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項的子項目，則會傳回 <xref:Microsoft.Office.Interop.Word.XMLNode> 物件，而非 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。  如需詳細資訊，請參閱[主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## 將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項不支援資料繫結 \(Data Binding\)。  這是因為 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項沒有複雜資料繫結能力，而簡單資料繫結無法表示重複的資料。  
  
## 格式  
 任何可套用至文件中文字的格式，都可套用至 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。  
  
## 事件  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項可以使用的事件為：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## 比較事件  
 您可以在使用者於特定 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項內容中移動游標時擷取事件。  例如，您可能有名為 `Customer` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項，該控制項有名為 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes> 子控制項，而 `Company` 有名為 `CompanyName` 和 `CompanyRegion` 的兩個 <xref:Microsoft.Office.Tools.Word.XMLNodes> 子控制項，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果每當游標移至 `Company` 節點內，您就要在執行窗格上顯示控制項，則游標是否放在 `CompanyName` 或 `CompanyRegion` 中都應該無關，因為這兩者都是在 `Company` 的內容中。  此時，您可以在 `Company` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件中撰寫程式碼。  
  
 在大部分情況下，當游標進入 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項時，會同時引發 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 和 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件，  下表說明這些事件之間的差異。  
  
|Select 事件|ContextEnter 事件|  
|---------------|---------------------|  
|當游標放在 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的其中一個節點時發生。|當游標從節點內容以外的區域，放到 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的其中一個節點或子代 \(Descendant\) 節點時發生。  換句說，它只有在內容變更時才會引發，而且可能因為多個巢狀 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項而引發。|  
  
 例如，當您將游標從 `Customer` 外部移至 `CompanyName` 內時，會引發 `Customer`、`Company` 和 `CompanyName` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件。  如果您接著將游標從 `CompanyName` 移至 `CompanyRegion`，則只會引發 `CompanyRegion` 的 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 事件，因為 `Company` 和 `Customer` 所處的內容都是一樣的。  您的文件中可以有多個 `Company` 節點。  如果您將游標從一個 `Company` 的 `CompanyName` 節點，移至另一個 `Company` 的 `CompanyName` 節點，則由於內容相同，因此只會引發 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 事件。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> 事件和 <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> 事件之間也存在相同的差異。  
  
## 請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode 控制項](../vsto/xmlnode-control.md)   
 [如何：將 XMLNodes 控制項加入至 Word 文件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [如何：在 Visual Studio 內將結構描述對應至 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  