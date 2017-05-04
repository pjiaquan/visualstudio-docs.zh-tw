---
title: "如何：將現有的 BDC 模型檔案加入至 SharePoint 專案 | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 匯入模型"
  - "BDC [Visual Studio 中的 SharePoint 開發], 移除模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 匯入模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 重複使用模型"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：將現有的 BDC 模型檔案加入至 SharePoint 專案
  您可以使用 Visual Studio 自訂、包裝和部署商務資料連接模型 \(BDC\)，將模型檔案 \(.bdcm\) 加入至任何 SharePoint 伺服器陣列專案。  如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
### 若要在 SharePoint 專案中加入 BDC 模型資源檔  
  
1.  在 \[**方案總管**\] 中，選取 SharePoint 專案的資料夾。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入現有項目**\]。  
  
3.  在 \[**加入現有項目**\] 對話方塊中，找到您要加入至專案之模型定義檔的位置，選擇檔案然後按下 \[**加入**\] 按鈕。  
  
     如果模型沒有定義「*.NET 組件類型的特定業務系統*」\(Line of Business \(LOB\) System of Type .NET Assembly\)，\[**加入 .NET 組件 LobSystem**\] 對話方塊就會出現。  
  
4.  如果對話方塊出現，請執行下列其中一個步驟：  
  
    -   如果您要撰寫自訂程式碼和使用設計工具來定義匯入之模型的中繼資料，請選擇 \[**是**\] 按鈕，命名系統，然後選擇 \[**確定**\] 按鈕。  
  
    -   否則，請選擇 \[**不**\] 按鈕，然後選擇 \[**確定**\] 按鈕。  
  
     \[**商務資料連接模型**\] 項目隨即加入至專案。  
  
## 請參閱  
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  