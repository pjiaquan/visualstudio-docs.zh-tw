---
title: "範例 Excel 延伸模組：TechnologyManager 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# 範例 Excel 延伸模組：TechnologyManager 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 類別，並負責提供 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 擴充功能的核心服務。  雖然基底類別有許多方法，但在這個範例中只使用其子集。  
  
 有些方法只是傳回屬性值。  許多這些方法是為了讓程式開發人員覆寫內建在自動程式碼 UI 測試引擎中的預設演算法。  這些方法會擲回 <xref:System.NotSupportedException> 或傳回 `null`，告知架構應使用預設演算法。  
  
 根據基礎技術的複雜度，開發技術管理員程式碼可能會需要數星期到數月之久。  Excel 提供機會讓您建立可能非常廣泛的技術管理員。  這個範例故意局限於 Excel 工作表和儲存格，只使用有限的格式。  
  
 可能的話，技術管理員程式碼會使用 `Communicator` 類別開啟的 .NET Remoting 通道，從執行於 Excel 處理序的增益集擷取資訊。  
  
## COM 可視性  
 請注意，這個類別和每個會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 類別的項目類別都有值為 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute>，以確定類別對 COM 是可見的。  
  
## TechnologyName 屬性  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> 屬性的這個覆寫必須提供唯一且有意義的名稱，可為擴充功能的每個其他元件識別基礎技術。  對於這個擴充功能，值為 "Excel"。  
  
## GetControlSupportLevel 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> 方法的這個覆寫會傳回數字，表示技術管理員可提供哪種支援層級給提供之控制代碼所代表的控制項。  傳回的值越高，技術管理員可支援控制項的層級就越高。  在這個案例中，方法會檢查包含控制項的視窗，如果它是 Excel 工作表，方法就會傳回最高的值，否則會傳回零，表示不提供任何支援。  
  
## 取得項目的方法  
 自動程式碼 UI 測試架構使用數個重要方法，取得技術特有的項目：藉由提供控制代碼、螢幕上的點或來自不同技術的項目。  這些方法程式碼的意義相當明顯。  基底方法如下：  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## ParseQueryId 方法  
 建立自動程式碼 UI 測試時，使用者可以針對測試中部分或全部控制項指定屬性值。  測試架構會使用這些屬性值，建立稱為搜尋屬性的名稱值組，用來在測試期間尋找特定 UI 控制項。  所有搜尋屬性一起代表技術中每個項目的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> 屬性值，其中包含每個控制項。  因為在測試期間可能必須多次尋找控制項，所以這個方法可以讓技術管理員以最佳方式針對指定的控制項剖析搜尋屬性。  這個方法也會傳回 Cookie，架構後續搜尋該控制項時可以使用它。  這個方法實作使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法剖析搜尋屬性。  
  
## MatchElement 方法  
 若要使用技術管理員搜尋控制項，您可以實作 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> 方法，傳回內含可能相符項目的陣列，或擲回 <xref:System.NotSupportedException> 告知架構使用自己的搜尋演算法。  無論哪一種方式，您都必須實作 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> 方法，而這個實作同樣會使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法。  
  
## 巡覽方法  
 這些方法會從 UI 階層取得提供之項目的父代、子系或同層級。  程式碼很簡單並有清楚的註解。  
  
## GetExcelElement 內部方法  
 這個內部方法會取得 Excel 項目的視窗控制代碼和資訊，並傳回要求的 Excel 項目。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [擴充自動程式碼 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)