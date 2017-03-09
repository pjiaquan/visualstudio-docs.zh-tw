---
title: "如何：停用 ClickOnce 應用程式的 URL 啟動過程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, URL 啟動"
  - "disallowUrlActivation"
  - "URL 啟動, ClickOnce 應用程式"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：停用 ClickOnce 應用程式的 URL 啟動過程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

一般而言，從 Web 伺服器安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式後，其將立即自動啟動。  基於安全性理由，您可以決定停用此行為，並告知使用者改從 \[開始\] 功能表啟動應用程式。  下列程序描述如何停用 URL 啟用。  
  
 這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，其來自 Web 伺服器。  此技術不得用於僅限線上使用的應用程式，其只能使用 URL 啟動。  如需僅限線上使用及已安裝應用程式之間差異的詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此程序使用 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 工具 MageUI.exe。  如需這項工具的詳細資訊，請參閱[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)。  您也可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 執行這項程序。  
  
## 程序  
  
#### 若要停用應用程式的 URL 啟用  
  
1.  開啟 MageUI.exe 中的部署資訊清單。  如果您尚未建立任何清單，請依照[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)進行。  
  
2.  選取 \[部署選項\] 索引標籤。  
  
3.  清除 \[安裝後自動執行應用程式\] 核取方塊。  
  
4.  儲存並簽署該資訊清單。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)