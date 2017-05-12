---
title: "BDC 模型設計工具概觀"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], BDC 總管"
  - "BDC [Visual Studio 中的 SharePoint 開發], 設計工具"
  - "BDC [Visual Studio 中的 SharePoint 開發], 方法詳細資料"
  - "BDC [Visual Studio 中的 SharePoint 開發], 視覺化工具"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], BDC 總管"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 設計工具"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 方法詳細資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 視覺化工具"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# BDC 模型設計工具概觀
  若要設計商務資料連接 \(BDC\) 模型，您可以使用 \[BDC 設計工具\]、\[**BDC 方法詳細資料**\] 視窗和 \[**BDC 總管**\] 來達成目的。  
  
 \[**BDC 總管**\] 可讓您瀏覽模型、搜尋模型以及定義型別描述元。  
  
## BDC 設計工具  
 \[BDC 設計工具\] 可以讓您定義模型中的實體，並以視覺化的方式排列它們之間的關聯性。  您可以使用 \[BDC 設計工具\] 完成下列工作：  
  
-   在模型中加入實體。  
  
-   從模型中移除實體。  
  
-   定義實體之間的關聯性。  
  
 若要開啟 BDC 設計工具中，按兩下專案中的模型檔案或開啟模型檔案的捷徑功能表，然後選擇 \[**開啟**\]。  將 \[**實體**\] 從 \[**工具箱**\] 拖曳或複製至設計工具，即可將實體加入模型中。  若要建立兩個實體之間的關聯性，請選擇 \[**工具箱**\] 中的 \[**關聯性**\] 控制項， 選擇第一個實體，然後再選擇第二個。  
  
## BDC 方法詳細資料視窗  
 您可以使用 \[**BDC 方法詳細資料**\] 視窗，定義方法的參數、執行個體和篩選描述元。  
  
 您可以在 \[**BDC 方法詳細資料**\] 視窗中快速產生「搜尋」、「特定搜尋」、「更新者」和「刪除者」方法。  產生這些方法時，Visual Studio 會將中繼資料 \(例如參數、執行個體和型別描述元\) 加入至方法，  您可以修改此中繼資料以滿足特定案例的要求。  
  
 若要開啟 \[**BDC 方法詳細資料**\] 視窗，請在功能表列上選擇 \[**檢視**\]、\[**其他視窗**\]、\[**BDC 方法詳細資料**\]。  
  
 若要檢視 \[**BDC 方法詳細資料**\] 視窗中的方法，請選取 \[BDC 設計工具\] 中的實體，  您選取之實體的方法隨即顯示在 \[**BDC 方法詳細資料**\] 視窗中。  如果沒有在 \[BDC 設計工具\] 中選取實體，\[**BDC 方法詳細資料**\] 視窗就不會顯示任何資訊。  
  
 請展開或摺疊 \[**BDC 方法詳細資料**\] 視窗中的節點，以定義參數、執行個體和篩選描述元。  您可以使用 \[**BDC 總管**\] 來定義型別描述元。  
  
## BDC 總管  
 \[**BDC 總管**\] 會顯示構成模型的元素。  若要開啟 \[**BDC 總管**\]，請在功能表列上，選擇 \[**檢視**\]、\[**其他視窗**\]、\[**BDC 總管**\]。  若要瀏覽模型，請展開 \[**BDC 總管**\] 中的節點，  每個節點均代表模型檔案之 XML 中的各個項目。  
  
 當您在 \[**BDC 總管**\] 中選取節點時，所選擇的每個節點之屬性會出現在 \[**屬性**\] 視窗中。  這些屬性大部分都對應至模型檔案中的屬性。  您可以使用 \[**BDC 總管**\] 上方的搜尋方塊來搜尋模型。  
  
> [!NOTE]  
>  \[**BDC 總管**\] 不會顯示識別項、自訂屬性、當地語系化字串、關聯群組、動作、篩選描述元、動作控制項清單及預設參數值。  
  
### 定義型別描述元  
 您可以使用 \[**BDC 總管**\] 來定義型別描述元。  \[BDC 總管\] 可讓您定義型別描述元一次，然後在模型中的其他位置重複使用該型別描述元。  若要達成此目的，請複製型別描述元並將它貼到任何其他參數或型別描述元上。  
  
> [!NOTE]  
>  如果變更原始型別描述元的內容，並不會影響該型別描述元的複本。  
  
 如需詳細資訊，請參閱[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## 請參閱  
 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)   
 [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  