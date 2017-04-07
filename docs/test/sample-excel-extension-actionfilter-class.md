---
title: "範例 Excel 擴充功能：ActionFilter 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
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
ms.openlocfilehash: dc4805133aef7247e25ac4de123de084d5918304
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-actionfilter-class"></a>範例 Excel 擴充功能：ActionFilter 類別
這個個內部類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 類別，並且表示 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 項目上測試動作的篩選條件。  
  
## <a name="simple-properties"></a>簡單屬性  
 這些唯讀屬性可讓開發人員指定自動程式化 UI 測試架構執行此測試動作篩選條件的方式。 例如，<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> 屬性會提供動作篩選條件的名稱。 其他屬性會取得動作篩選條件的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>，以及此測試動作篩選條件所篩選之測試動作的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 名稱。 其他則會指出是否要進行 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>，以及測試動作是否為 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>。  
  
## <a name="processrule-method"></a>ProcessRule 方法  
 這個方法是由自動程式化 UI 測試架構所呼叫，會針對提供的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> 執行篩選條件。 這個特定的覆寫會在堆疊中的下一個動作傳送按鍵動作至儲存格時，移除儲存格上的滑鼠選擇動作。 然後它會傳回 `false`。  
  
## <a name="private-methods"></a>私用方法  
 `IsLeftClick` 方法會判斷提供的動作是否代表按下滑鼠左鍵。 `AreActionsOnSameExcelCell` 方法會判斷兩個提供的動作是否在 Excel 中的同一個儲存格上執行。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

