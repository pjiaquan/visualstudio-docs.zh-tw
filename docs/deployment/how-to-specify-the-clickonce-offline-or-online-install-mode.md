---
title: "如何：指定 ClickOnce 離線或線上安裝模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce 部署, 指定安裝模式"
  - "ClickOnce 安裝模式"
  - "安裝模式"
  - "離線應用程式"
  - "線上應用程式"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：指定 ClickOnce 離線或線上安裝模式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的 `Install Mode` 決定應用程式將在離線或線上使用。  當您選擇 \[**應用程式只能在線上時使用**\] 時，使用者必須可以存取 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發行位置 \(Web 網頁或檔案共用\)，才能執行應用程式。  當您選擇 \[**應用程式也可以在離線時使用**\] 時，應用程式就會將項目加入至 \[**開始**\] 功能表和 \[**新增或移除程式**\] 對話方塊；使用者未連線時，也可以執行應用程式。  
  
 在 \[**專案設計工具**\] 的 \[**發行**\] 頁面上，可以設定 `Install Mode`。  
  
 **注意**：也可以使用發行精靈設定 `Install Mode`。  如需詳細資訊，請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
### 若要讓 ClickOnce 應用程式只能在線上時使用  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  在 \[**安裝模式設定**\] 區域中，按一下 \[**應用程式只能在線上時使用**\] 選項按鈕。  
  
### 若要讓 ClickOnce 應用程式在線上或離線時都可以使用  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  在 \[**安裝模式設定**\] 區域中，按一下 \[**應用程式也可以在離線時使用**\] 選項按鈕。  
  
     安裝時，應用程式就會將項目加入至 \[**開始**\] 功能表，以及 \[控制台\] 中的 \[**新增或移除程式**\]。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)