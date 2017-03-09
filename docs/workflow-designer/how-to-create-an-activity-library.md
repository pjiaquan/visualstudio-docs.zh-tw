---
title: "HOW TO：建立活動程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# HOW TO：建立活動程式庫
自訂活動是用來將工作流程中特定的商務程序模型化。[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中提供了活動程式庫範本，可讓您透過 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 來以視覺方式建立這類自訂活動。  
  
### 若要建立工作流程活動程式庫  
  
1.  啟動 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**新增**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**專案類型**\] 窗格中，選取 \[**Visual C\#**\] 專案或 \[**Visual Basic**\] 群組中的 \[**工作流程**\]，視您的語言偏好而定。  
  
4.  選取 \[**範本**\] 窗格中的 \[**活動程式庫**\]。  
  
5.  在 \[**名稱**\] 方塊中，輸入專案的描述性名稱，讓專案更容易識別。  
  
6.  在 \[**位置**\] 方塊中，輸入用來儲存專案的目錄，或按一下 \[**瀏覽**\] 以巡覽至該目錄。  
  
7.  在 \[**方案**\] 方塊中，輸入方案的描述性名稱，然後按一下 \[**確定**\]。  
  
    > [!NOTE]
    >  如果您要將工作流程主控台應用程式加入至現有的方案，請在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中開啟該方案，並在 \[**方案總管**\] 中以滑鼠右鍵按一下此方案，然後依序選取 \[**新增**\] 和 \[**新增專案**\]，開啟 \[**新增專案**\] 對話方塊。依照本程序上面的說明繼續進行。  
  
8.  專案範本會以 XAML 格式建立活動定義。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 會開啟並顯示自訂活動的畫布。  
  
9. 將 \[**工具箱**\] 中的活動拖曳至設計介面，以包含於您的自訂活動。  
  
    > [!CAUTION]
    >  自訂活動的主體中僅可有一個子活動，但是該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。  
  
## 請參閱  
 [HOW TO：建立活動](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)