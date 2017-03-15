---
title: "HOW TO：建立 WCF 工作流程服務應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# HOW TO：建立 WCF 工作流程服務應用程式
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 工作流程服務應用程式是分散式通訊服務，可在用戶端與服務本身之間傳遞訊息，並跨越處理序界限。服務端的服務合約實作是採用類似 .NET Framework 3.5 舊版工作流程服務的方式，透過 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 中的工作流程活動來宣告完成。  
  
### 若要建立 WCF 工作流程服務應用程式  
  
1.  啟動 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**新增**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**已安裝的範本**\] 窗格中，選取 \[**Visual C\#**\] 或 \[**Visual Basic**\] 群組中的 \[**WCF**\] 或 \[**工作流程**\]，視您的語言選擇而定。  
  
4.  在中間的窗格中，選取 \[**WCF 工作流程服務應用程式**\]。  
  
5.  在 \[**名稱**\] 方塊中，輸入專案的描述性名稱，讓專案更容易識別。  
  
6.  在 \[**位置**\] 方塊中，輸入用來儲存專案的目錄，或按一下 \[**瀏覽**\] 來巡覽找到它。  
  
7.  在 \[**方案**\] 方塊中選取它來建立新的方案，然後按一下 \[**確定**\]。  
  
    > [!NOTE]
    >  如果您要將工作流程主控台應用程式加入至現有的方案，請在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中開啟該方案，並在 \[**方案總管**\] 中以滑鼠右鍵按一下此方案，然後依序選取 \[**新增**\] 和 \[**新增專案**\]，開啟 \[**新增專案**\] 對話方塊。依照本程序上面的說明繼續進行。  
  
8.  專案範本會以 XAML 格式建立服務定義。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 會開啟設計檢視，其中有包含一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.Activities.Statements.Sequence> 活動。  
  
## 請參閱  
 [HOW TO：建立活動](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)