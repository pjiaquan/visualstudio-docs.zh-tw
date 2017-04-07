---
title: "範例 Excel 擴充功能：Element 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 396960f31c60318833b8171a4e17595db6ff9fca
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-element-classes"></a>範例 Excel 擴充功能：Element 類別
此擴充功能使用衍生自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 的類別，代表 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 中的工作表控制項和儲存格控制項。  
  
 這個擴充功能的基底項目是 `ExcelElement`。 `ExcelWorksheetElement` 類別和 `ExcelCellElement` 類別都繼承自該項目  
  
## <a name="element-and-elementinformation-classes"></a>Element 和 ElementInformation 類別  
 `Element` 是 Excel 擴充功能所有使用者介面項目的基底類別，繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 類別。 `ElementInformation` 是範例中項目資訊類別的基底類別，它並沒有成員。  
  
#### <a name="simple-properties-and-methods"></a>簡單屬性和方法  
 這些成員會傳回簡單值，例如 `Name` 屬性的值或 `ClassName` 屬性的值，而且程式碼很清楚易讀。 有些值是透過 `Utility` 類別傳回，稍後將予以討論。 其他會傳回 `null`，因為它們與這個範例擴充功能並不相關。 有兩個成員值得說明：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 屬性和 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> 方法。  
  
#### <a name="queryid-property"></a>QueryId 屬性  
 這個屬性傳回的條件是由屬性名稱值組所構成，會在播放期間唯一識別控制項。 針對每個衍生的控制項類別，程式開發人員必須覆寫這個屬性，以傳回架構可用來尋找 UI 控制項的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> 物件。  
  
#### <a name="cacheproperties-method"></a>CacheProperties 方法  
 這個方法是由測試架構在錄製程序期間呼叫，以便告知項目儲存重要屬性的快照。 即使實際 UI 控制項不再顯示在螢幕上，這也會讓屬性保持可用。  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement 和 WorksheetInformation 類別  
 `WorksheetElement` 類別代表測試架構中的 Excel 工作表，是繼承自 `Element` 基底類別。 它覆寫三個屬性以提供 Excel 工作表物件的特定資訊：<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>，以及 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>。  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 也會套用至這個類別，以使它針對 COM 為可見。  
  
 `WorksheetInformation` 類別代表 Excel 工作表的相關資訊。 它只有一個成員，也就是 `SheetName` 屬性，這對這個範例而言已經夠用。  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellElement 和 CellInformation 類別  
 `CellElement` 類別代表 Excel 儲存格，是繼承自 `Element` 基底類別。 唯一的覆寫成員是 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 屬性，該屬性會傳回 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>，它會使用 `RowIndex` 和 `ColumnIndex` 屬性來識別儲存格。  
  
## <a name="utilities-and-excelutilities-classes"></a>Utilities 和 ExcelUtilities 類別  
 內部 `ExcelUtilities` 類別提供一些常數值 (例如技術名稱)，以及判斷提供的視窗控制代碼是否代表 Excel 工作表的方法。  
  
 `Utilities` 類別有 Helper 方法，會傳回 UI 的各種資訊。 有些方法會透過直接呼叫外部系統 DLL (例如 **USER32.DLL** 和 **OLEACC.DLL**)，從 UI 取得視窗控制代碼**。**  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

