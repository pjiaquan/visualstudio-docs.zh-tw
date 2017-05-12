---
title: "如何：新增資源檔"
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
  - "資源檔 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 資源檔"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：新增資源檔
  新增資源檔的命令位於 \[方案總管\] 中方案節點和功能節點的捷徑功能表上。  如需詳細資訊，請參閱[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
### 若要將全域資源檔加入至 SharePoint 方案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，開啟 SharePoint 方案。  
  
2.  在 \[**方案總管**\] 中，選擇 SharePoint 專案節點，然後在功能表列上選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，選擇 \[**全域資源檔**\] 範本，然後選擇 \[**確定**\] 按鈕。  
  
    > [!NOTE]  
    >  只有當選取 SharePoint 專案項目時，\[全域資源檔\] 專案項目範本才會出現。  
  
4.  在 \[**加入資源**\] 對話方塊中，選取資源檔的文化特性，例如英文 \(美國\)。  
  
     此步驟會將全域資源檔以 Resource*x***.***culture***.**resx 的格式 \(例如 Resource1.en\-US.resx\) 加入至您的方案。  
  
5.  當 \[**資源編輯器**\] 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中開啟，請將資源加入至資源檔。  
  
### 若要將功能資源檔加入至 SharePoint 功能  
  
1.  如果 SharePoint 方案尚未在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟，請開啟方案。  
  
2.  在 \[**方案總管**\] 中，開啟功能名稱的捷徑功能表 \(會在 \[**功能**\] 節點下\)，然後選取 \[**新增功能資源**\]。  
  
     這個步驟會將資源檔以 *ResourceFileName***.***culture***.**resx 的格式 \(例如 Feature1.en\-US.resx\) 加入至功能。  
  
3.  當 \[**資源編輯器**\] 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中開啟，請將資源加入至資源檔。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  