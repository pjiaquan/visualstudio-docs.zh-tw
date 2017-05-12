---
title: "如何：加入專案輸出參考"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "專案輸出參考 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 進階封裝工具"
  - "Visual Studio 中的 SharePoint 開發, 專案輸出參考"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：加入專案輸出參考
  若要將非 SharePoint 專案組件 \(或 Silverlight 專案中的 .xap 檔案\) 部署至 SharePoint，請將其做為專案輸出參考加入。  
  
 這個程序會建立兩個專案之間的方案建置相依性。  在建置和部署 SharePoint 專案之前，建置與專案輸出參考相關聯的專案。  
  
### 若要加入專案輸出參考  
  
1.  載入至少包含一個 SharePoint 專案和一個非 SharePoint 專案的方案。  
  
2.  在 \[**方案總管**\] 中，選擇 SharePoint 專案節點的一個項目。  
  
3.  在 \[**屬性**\] 視窗中選擇 \[**專案輸出參考**\] 屬性，然後按下其旁邊的省略符號 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\) 按鈕。  
  
4.  在 \[**專案輸出參考**\] 對話方塊中選擇 \[**加入**\] 按鈕。  
  
5.  在屬性窗格中，選擇 \[**部署類型**\] 屬性旁邊的下拉箭號，並為您所參考的非 SharePoint 項目選取適當值，例如 \[**ElementFile**\]。  
  
6.  選取 \[**專案名稱**\] 旁邊的箭號，並選取非 SharePoint 專案項目的名稱，然後選擇 \[**好**\] 按鈕。  
  
## 請參閱  
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  