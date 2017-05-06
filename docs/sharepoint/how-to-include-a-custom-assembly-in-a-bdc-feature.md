---
title: "如何：在 BDC 功能中包含自訂組件"
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
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 加入參考"
  - "BDC [Visual Studio 中的 SharePoint 開發], 自訂組件"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 加入參考"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 自訂組件"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：在 BDC 功能中包含自訂組件
  專案可以參考相同方案中其他專案的組件。  不過，您必須使用 \[**將被參考組件指派給 LobSystem**\] 對話方塊將這些組件加入至專案的功能檔案。  
  
### 若要將自訂組件納入商務資料連接模型 \(BDC\) 功能中  
  
1.  在 \[**方案總管**\] 中，選取包含 BDC 模型的資料夾。  
  
2.  在 \[**檢視**\] 功能表中，按一下 \[**屬性視窗**\]。  
  
3.  在 \[**屬性視窗**\] 中，選取 \[**Assemblies**\] 屬性，然後選擇省略符號按鈕 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\)。  
  
     \[**將被參考組件指派給 LobSystem**\] 對話方塊隨即出現。  
  
4.  在 \[**選取組件**\] 清單中，選取自訂組件。  
  
    > [!NOTE]  
    >  您必須先新增包含該組件之專案的參考，組件才會出現在 \[**將被參考組件指派給 LobSystem**\] 對話方塊中。  如需詳細資訊，請參閱[如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
5.  在 \[**參考屬性**\] 群組中，開啟 \[**LobSystem 範圍**\] 屬性的清單，選取要使用自訂組件之方法的 LOB 系統，然後選擇 \[**確定**\] 按鈕。  
  
    > [!NOTE]  
    >  若要對自訂組件中的程式碼進行偵錯，您必須將該組件加入至方案套件。  如需詳細資訊，請參閱[如何：新增與移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
## 請參閱  
 [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  