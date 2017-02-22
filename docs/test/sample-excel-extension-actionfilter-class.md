---
title: "範例 Excel 延伸模組：ActionFilter 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# 範例 Excel 延伸模組：ActionFilter 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個內部類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 類別，並且表示 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 項目上測試動作的篩選條件。  
  
## 簡單屬性  
 這些唯讀屬性可讓開發人員指定自動程式碼 UI 測試架構執行此測試動作篩選條件的方式。  例如，<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> 屬性會提供動作篩選條件的名稱。  其他屬性會取得動作篩選條件的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>，以及此測試動作篩選條件所篩選之測試動作的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 名稱。  其他則會指出是否 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>，以及測試動作是否為 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>。  
  
## ProcessRule 方法  
 這個方法是由自動程式碼 UI 測試架構所呼叫，會針對提供的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> 執行篩選條件。  這個特殊的覆寫會在堆疊中的下一個動作傳送按鍵動作至儲存格時，移除儲存格上的滑鼠點選動作。  然後它會傳回 `false`。  
  
## 私用方法  
 `IsLeftClick` 方法會判斷提供的動作是否代表按下滑鼠左鍵。  `AreActionsOnSameExcelCell` 方法會判斷兩個提供的動作是否在 Excel 中的同一個儲存格上執行。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [擴充自動程式碼 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)