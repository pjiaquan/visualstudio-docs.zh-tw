---
title: "HOW TO：建立循序工作流程主控台應用程式 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "主控台應用程式, 循序工作流程"
  - "循序工作流程, 主控台應用程式"
  - "工作流程, 主控台應用程式"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# HOW TO：建立循序工作流程主控台應用程式 (舊版)
依照下列步驟使用 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 提供的舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 來建立循序工作流程主控台應用程式專案。當您需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
### 若要建立循序工作流程主控台應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**新增**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**新增專案**\] 視窗上方的下拉式清單中，選取 \[**.NET Framework 3.0**\] 選項或 \[**.NET Framework 3.5**\] 選項，以存取舊版設計工具。  
  
    > [!NOTE]
    >  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的預設選項是 \[**.NET Framework 4**\]。這個選項是用來建立以 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 為目標的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式，而不會使用舊版設計工具。  
  
4.  在 \[**專案類型**\] 窗格中，選取 Visual C\# 專案或 Visual Basic 專案 \(在 \[**其他語言**\] 底下\)，然後選取 \[**工作流程**\]。  
  
5.  在 \[**範本**\] 窗格中，選取 \[**循序工作流程主控台應用程式**\]。  
  
6.  在 \[**名稱**\] 方塊中，輸入專案的描述性名稱，讓專案更容易識別。  
  
7.  在 \[**位置**\] 方塊中，輸入用來儲存專案的目錄，或按一下 \[**瀏覽**\] 來巡覽找到它。  
  
     接著會開啟 Windows Form 設計工具，顯示您剛剛建立之專案的 Form1。  
  
8.  按一下 \[**確定**\]。  
  
     工作流程設計工具會開啟並顯示您所建立的循序工作流程之設計介面。  
  
9. 將 \[**工具箱**\] 中的活動拖曳至 \[**拖放活動**\] 指定區域中的設計介面。  
  
## 請參閱  
 [建立舊版工作流程活動](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/zh-tw/557bcb1f-a7ab-49f6-8df7-2706b7001301)