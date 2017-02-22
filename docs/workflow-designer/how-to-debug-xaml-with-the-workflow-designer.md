---
title: "HOW TO：使用工作流程設計工具偵測 XAML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# HOW TO：使用工作流程設計工具偵測 XAML
工作流程是根據 XAML 所定義的。工作流程的 UI 呈現方式，乃是建立在定義該工作流程的 XAML 樹狀結構上。偵錯的體驗類似 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的工作流程偵錯。例如，為 XAML 偵錯時，其區域變數、監看及執行緒視窗的運作方式，就像在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中偵錯一樣。此外，在 XAML 偵錯期間的呼叫堆疊檢視，也是工作流程執行流程的逐行階層架構檢視。  
  
> [!NOTE]
>  如果為工作流程的 XAML 與活動位於同一個組件中，則不會包含類別名稱中的組件部分。沒有類別 \(活動\) 名稱的這個部分，就不能在執行階段載入 XAML。不建議在與主要專案的同一個命名空間中定義活動，否則，XAML 在設計工具中編輯之後必須手動編輯。  
  
### 若要進行工作流程 XAML 偵錯  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟工作流程或活動專案。  
  
2.  在您要偵錯的一個或多個活動上設定中斷點，如 [HOW TO：在工作流程中設定中斷點](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)所述。  
  
3.  以滑鼠右鍵按一下包含您工作流程定義的 .xaml 檔案，然後選取 \[**檢視程式碼**\]。在設計檢視中設定中斷點的活動之後，您會看到該活動 XAML 項目宣告的同一行上顯示中斷點。  
  
4.  如 [HOW TO：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)所述，叫用偵錯工具。  
  
5.  當程式碼執行到您的其中一個中斷點時，該中斷點關聯的 XAML 項目會出現醒目顯示。若要移至下一個中斷點，請使用 **F10** 或 **F11** 鍵。  
  
## 請參閱  
 [HOW TO：在工作流程中設定中斷點](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [HOW TO：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)