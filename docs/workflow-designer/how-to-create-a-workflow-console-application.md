---
title: "HOW TO：建立工作流程主控台應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# HOW TO：建立工作流程主控台應用程式
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 可讓您建立執行系統或人工處理序的工作流程。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 會提供建立這些工作流程的設計介面。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 可用來從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建立工作流程，或者可以整合到重新裝載設計工具的其他應用程式中。  
  
 本主題描述如何在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中使用 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 建立主控台應用程式中的工作流程。  
  
### 若要建立工作流程主控台應用程式  
  
1.  啟動 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**新增**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**已安裝的範本**\] 窗格中，選取 \[**Visual C\#**\] 或 \[**Visual Basic**\] 群組中的 \[**工作流程**\]，視您的語言偏好而定。  
  
4.  在中間的窗格中，選取 \[**工作流程主控台應用程式**\]。  
  
5.  在 \[**名稱**\] 方塊中，輸入專案的描述性名稱，讓專案更容易識別。  
  
6.  在 \[**位置**\] 方塊中，輸入用來儲存專案的目錄，或按一下 \[**瀏覽**\] 來巡覽找到它。  
  
7.  在 \[**方案**\] 方塊中，輸入新方案的名稱。按一下 \[**確定**\] 建立應用程式。  
  
    > [!NOTE]
    >  如果您要將工作流程主控台應用程式加入至現有的方案，請在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中開啟該方案，並在 \[**方案總管**\] 中以滑鼠右鍵按一下此方案，然後依序選取 \[**新增**\] 和 \[**新增專案**\]，開啟 \[**新增專案**\] 對話方塊。依照本程序上面的說明繼續進行。  
  
8.  專案範本會以 XAML 建立工作流程定義，而主控台應用程式定義會使用原始程式碼。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 會開啟並顯示您所建立之工作流程的畫布。  
  
9. 若要撰寫工作流程，請從 \[**工具箱**\] 將活動或其他工作流程項目拖曳到工作流程中的設計介面。  
  
## 請參閱  
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)