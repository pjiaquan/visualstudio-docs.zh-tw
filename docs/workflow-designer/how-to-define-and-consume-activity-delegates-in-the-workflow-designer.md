---
title: "HOW TO：定義並取用工作流程設計工具中的活動委派 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：定義並取用工作流程設計工具中的活動委派
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)]包含用於 <xref:System.Activities.Statements.InvokeDelegate> 活動的全新設計工具。這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。  
  
### 定義活動委派  
  
1.  在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，依序選取 \[**檔案**\]、\[**新增**\]、\[**專案**\]。選取位在左側的 \[**工作流程**\] 節點和位在右側的 \[**工作流程主控台應用程式**\]。為專案命名 \(如有需要\)，然後按一下 \[**確定**\]。  
  
2.  以滑鼠右鍵按一下 \[**方案總管**\] 中的專案，並選取 \[**加入**\]、\[**新增項目**\]。選取位在左側的 \[**工作流程**\] 節點和位在右側的 \[**活動**\]。將新活動命名為 **MyForEach.xaml**，然後按一下 \[**確定**\]。活動會在工作流程設計工具中開啟。  
  
3.  在工作流程設計工具中，按一下 \[**引數**\] 索引標籤。  
  
4.  按一下 \[**建立引數**\]。將新引數命名為 **Items**。  
  
5.  在 \[**引數型別**\] 資料行中，選取 \[**\[T\] 陣列**\]。  
  
6.  在型別瀏覽器中，選取 \[**Object**\]。按一下 \[**確定**\]。  
  
7.  再按一下 \[**建立引數**\]。將新引數命名為 **Body**。在新引數的 \[**方向**\] 資料行中，選取 \[**屬性**\]。  
  
8.  在 \[引數型別\] 資料行中，選取 \[**瀏覽型別**\]  
  
9. 在型別瀏覽器中，於 \[**型別名稱**\] 欄位中輸入 **ActivityAction**。選取樹狀檢視中的 **ActivityAction\<T\>**。在出現的下拉式清單中選取 \[**Object**\]，將型別 **ActivityAction\<Object\>** 指派給引數。  
  
10. 將工具箱中 \[**控制流程**\] 區段的 <xref:System.Activities.Statements.While> 活動拖曳至設計工具介面上。  
  
11. 選取 <xref:System.Activities.Statements.While> 活動，然後選取 \[**變數**\] 索引標籤。  
  
12. 選取 \[**建立變數**\]。將新變數命名為 **Index**。  
  
13. 在 \[**變數型別**\] 資料行中，選取 **Int32**。 將 \[**範圍**\] 保留為 \[**While**\]，以及將 \[**預設**\] 資料行保留為空的。  
  
14. 將 <xref:System.Activities.Statements.While> 活動的 \[**Condition**\] 屬性設為 **index \< Items.Length;**。  
  
15. 將工具箱中 \[**基本**\] 區段的 <xref:System.Activities.Statements.InvokeDelegate> 活動拖曳至<xref:System.Activities.Statements.While> 活動的 \[**主體**\] 上。  
  
16. 選取委派下拉式清單中的 \[**主體**\]。  
  
17. 在 <xref:System.Activities.Statements.InvokeDelegate> 活動的 \[**屬性**\] 窗格中，按一下 \[**委派引數**\] 屬性中的 **…** 按鈕。  
  
18. 在名為 **Argument** 的引數的 \[**值**\] 資料行中，輸入 **Items\[Index\]**。按一下 \[**確定**\]，關閉 \[**DelegateArguments**\] 對話方塊。  
  
19. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。會建立 <xref:System.Activities.Statements.Assign>，而且會自動建立 <xref:System.Activities.Statements.Sequence> 活動以包含 **MyForEach** 活動的 \[**主體**\] 區段中的兩個活動。需要此序列，因為 \[**主體**\] 區段只能包含單一活動。自動建立新的<xref:System.Activities.Statements.Sequence>活動是 [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 的新功能。  
  
20. 將 <xref:System.Activities.Statements.Assign> 活動的 \[**To**\] 屬性設為 **index**。將 \[**Assign**\] 活動的 \[**Value**\] 屬性設為 **index\+1**。  
  
 自訂 **MyForEach** 活動現在會針對每個透過 **Items** 集合傳遞到它的值叫用一次任意活動，集合中的值做為活動的輸入。  
  
### 使用工作流程中的自訂活動  
  
1.  按下 **Ctrl\+Shift\+B** 建置此專案。  
  
2.  在 \[**方案總管**\] 中，開啟設計工具中的 **Workflow1.xaml**。  
  
3.  從工具箱將 **MyForEach** 活動拖曳至設計工具介面。活動將會在工具箱的區段中，名稱與專案的名稱相同。  
  
4.  將 **MyForEach** 活動的 \[**Items**\] 屬性設為 **new Object\[\] {1, "abc"}**。  
  
5.  將工具箱中 \[**基本**\] 區段的 <xref:System.Activities.Statements.WriteLine> 活動拖曳至**MyForEach** 活動的 \[**Delegate:Body**\] 區段。  
  
6.  將 <xref:System.Activities.Statements.WriteLine> 活動的 \[**Text**\] 屬性設為 **Argument.ToString\(\)**。  
  
 當執行工作流程時，主控台將顯示以下資訊：  
  
 **1**   
**abc**