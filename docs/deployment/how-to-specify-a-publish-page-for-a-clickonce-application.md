---
title: "如何：指定 ClickOnce 應用程式的發行頁面 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "ClickOnce 部署, 指定發行頁"
  - "部署應用程式 [ClickOnce], 指定發行頁"
  - "發行頁屬性"
  - "發行, ClickOnce"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：指定 ClickOnce 應用程式的發行頁面
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，會產生預設 Web 網頁 \(publish.htm\)，與應用程式一起發行。  這個網頁包含應用程式名稱、安裝應用程式和 \(或\) 必要條件的連結，以及描述 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的說明主題連結。  專案的 \[**發行頁**\] 屬性可讓您指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的網頁名稱。  
  
 一旦指定發行頁，下次發行時，就會將它複製到發行位置；再重新發行時，將不會覆寫它。  如果您要自訂網頁外觀，可以這麼做，而不需擔心失去變更。  如需詳細資訊，請參閱 [如何：自訂 ClickOnce 應用程式的預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。  
  
 在 \[**發行選項**\] 對話方塊中可以設定 \[**發行頁**\] 屬性 \(從 \[**專案設計工具**\] 的 \[**發行**\] 窗格存取\)。  
  
### 若要指定 ClickOnce 應用程式的自訂 Web 網頁  
  
1.  在 \[**方案總管**\] 中選取了專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  選取 \[**發行**\] 窗格。  
  
3.  按一下 \[**選項**\] 按鈕，開啟 \[**發行選項**\] 對話方塊。  
  
4.  按一下 \[**部署**\]。  
  
5.  在 \[**發行選項**\] 對話方塊中，確定已選取 \[**發行之後開啟部署網頁**\] 核取方塊 \(它預設應該是呈選取狀態\)。  
  
6.  在 \[**部署網頁:**\] 方塊中，輸入 Web 網頁名稱，再按一下 \[**確定**\]。  
  
### 若要防止每次發行時都啟動發行頁  
  
1.  在 \[**方案總管**\] 中選取了專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  選取 \[**發行**\] 窗格。  
  
3.  按一下 \[**選項**\] 按鈕，開啟 \[**發行選項**\] 對話方塊。  
  
4.  按一下 \[**部署**\]。  
  
5.  在 \[**發行選項**\] 對話方塊中，清除 \[**發行之後開啟部署網頁**\] 核取方塊。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [如何：自訂 ClickOnce 應用程式的預設 Web 網頁](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)