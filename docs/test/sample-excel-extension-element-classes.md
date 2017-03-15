---
title: "範例 Excel 延伸模組：Element 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# 範例 Excel 延伸模組：Element 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此擴充功能使用衍生自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 的類別，代表 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 中的工作表控制項和儲存格控制項。  
  
 這個擴充功能的基底項目是 `ExcelElement`。  `ExcelWorksheetElement` 類別和 `ExcelCellElement` 類別繼承自該項目。  
  
## Element 和 ElementInformation 類別  
 `Element`  是此 Excel 擴充功能所有使用者介面項目的基底類別，繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 類別。  `ElementInformation` 是範例中項目資訊類別的基底類別，並沒有成員。  
  
#### 簡單屬性和方法  
 這些成員會傳回簡單值，例如 `Name` 屬性的值或 `ClassName` 屬性的值，而且程式碼很清楚易讀。  有些值是透過 `Utility` 類別傳回，稍後將予以討論。  有些會傳回 `null`，因為它們在這個範例擴充功能中是不相關的。  兩個成員值得說明：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 屬性和 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> 方法。  
  
#### QueryId 屬性  
 這個屬性傳回的條件是由屬性名稱值組所構成，會在播放期間唯一識別控制項。  針對每個衍生的控制項類別，程式開發人員必須覆寫這個屬性，以傳回架構可用來尋找 UI 控制項的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> 物件。  
  
#### CacheProperties 方法  
 這個方法是由測試架構在錄製程序期間呼叫，以便告知項目儲存重要屬性的快照。  即使實際 UI 控制項不再顯示在螢幕上，這也會讓屬性保持可用。  
  
## WorksheetElement 和 WorksheetInformation 類別  
 `WorksheetElement`  類別代表測試架構中的 Excel 工作表，是繼承自 `Element` 基底類別。  三個屬性會被覆寫以提供 Excel 工作表物件的特定資訊：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> 和 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>。  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 也會套用至這個類別，讓它對 COM 是可見的。  
  
 `WorksheetInformation`  類別代表 Excel 工作表的相關資訊。  它只有一個成員 `SheetName` 屬性，對這個範例而言是夠用的。  
  
## CellElement 和 CellInformation 類別  
 `CellElement`  類別代表 Excel 儲存格，是繼承自 `Element` 基底類別。  唯一覆寫的成員是 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 屬性，會傳回 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>，它可使用 `RowIndex` 和 `ColumnIndex` 屬性識別儲存格。  
  
## Utilities 和 ExcelUtilities 類別  
 內部 `ExcelUtilities` 類別提供一些常數值 \(例如技術名稱\)，以及判斷提供的視窗控制代碼是否代表 Excel 工作表的方法。  
  
 `Utilities`  類別有 Helper 方法，會傳回 UI 的各種資訊。  有些方法會透過直接呼叫外部系統 DLLs \(例如 **USER32.DLL** 和 **OLEACC.DLL**\)，從 UI 取得視窗控制代碼**.**  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [擴充自動程式碼 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)