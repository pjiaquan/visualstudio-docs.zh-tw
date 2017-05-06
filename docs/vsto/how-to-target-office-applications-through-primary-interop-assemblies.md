---
title: "如何：透過主要 Interop 組件以 Office 應用程式為目標"
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
helpviewer_keywords: 
  - "應用程式部署 [Visual Studio 中的 Office 程式開發], 自動化"
  - "組件 [Visual Studio 中的 Office 程式開發], PIA 參考"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 自動化"
  - "Visual Studio 中的 Office 主要 Interop 組件, 加入參考"
  - "主要 Interop 組件 [Visual Studio 中的 Office 程式開發], 加入參考"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：透過主要 Interop 組件以 Office 應用程式為目標
  當您建立新的 Office 專案時，Visual Studio 會自動將參考加入建置專案所需的 Microsoft Office 主要 Interop 組件 \(PIA\)。  在下列情節中，您必須將參考加入其他 PIA：  
  
-   您想使用專案中其他 Microsoft Office 應用程式的功能。  例如，您想將專案中的 Microsoft Office Excel 功能用於 Microsoft Office Word。  
  
-   您想在 Visual Studio 中自動化沒有專用專案的 Microsoft Office 應用程式 \(例如 Microsoft Office Access\)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 加入主要 Interop 組件的參考  
  
1.  開啟您的 Office 專案，並選取 \[方案總管\] 中的專案名稱。  
  
2.  在 \[專案\] 功能表上，按一下 \[加入參考\]。  
  
3.  在 \[架構\] 索引標籤上，選取 \[組件名稱\] 清單中您要的 PIA。  如需可用 Microsoft Office 主要 Interop 組件的詳細資訊，請參閱 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
     如果專案以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標，則根據預設，會將組件參考的 \[內嵌 Interop 類型\] 屬性設定為 \[True\]。  藉由使用這個項目，方案就不要求使用者電腦上須有 PIA。  如需詳細資訊，請參閱[設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。  
  
    > [!NOTE]  
    >  在 Office 專案中，一律使用 \[加入參考\] 對話方塊的 \[.NET\] 索引標籤 \(而不是使用 \[COM\] 索引標籤\) 來加入 Office PIA 的參考。  如需詳細資訊，請參閱 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
4.  按一下 \[**確定**\]。  
  
     組件名稱隨即出現在 \[方案總管\] 的 \[參考\] 資料夾中。  
  
## 請參閱  
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [如何：安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  